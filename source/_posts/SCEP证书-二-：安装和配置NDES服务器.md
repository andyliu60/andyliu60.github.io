---
title: 'SCEP证书(二)：安装和配置NDES服务器'
date: 2019-03-05 11:16:12
tags:
- Intune
categories:
- 企业产品
---
# 创建NDES服务账号

在域控制器中，打开**Active Directory Users and Computers**，创建域用户，用户名为**ndes**。

![](/images/239.png)

<!-- more -->

# 创建SCEP证书模板

1.  登陆CA服务器，打开MMC，并添加**Certificate Templates**。
2.  选择**User**模板，并复制该模板。

![](/images/240.png)

3. 该模板必须包含以下配置：



- In **General**:

	Confirm the **Publish certificate in Active Directory** property is not checked.

	Enter a friendly **Template display name** for the template.


- In **Subject Name**, select Supply in the request. (Security is enforced by the Intune policy module for NDES).


- In **Extensions**, confirm the **Description of Application Policies** includes **Client Authentication**.

	>>> For iOS and macOS certificate templates, on the **Extensions** tab, edit **Key Usage**, and confirm **Signature is proof of origin** is not selected.


- In Security, add the NDES service account, and give it Enroll permissions to the template. Intune admins who create SCEP profiles require Read rights so that they can browse to the template when creating SCEP profiles.

4. Review the **Validity period** on the **General** tab of the template.

Example template configuration:

![](/images/241.png)
![](/images/242.png)
![](/images/243.png)
![](/images/244.png)
![](/images/245.png)

5. 配置CA,运行证书请求者自行输入证书有效期：

		certutil -setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE
	
		net stop certsvc
	
		net start certsvc

6. 打开**Certificate Authority**管理面板，选择**Certificate Templates**并点击右键，点击**Action > New > Certificate Template to Issue**，发布创建的证书模板。

![](/images/246.png)


# 安装NDES角色

1. 准备一台全新的Windows Server 2016设备，打开**Server Manager**，安装NDES和IIS。

![](/images/247.png)
![](/images/248.png)
![](/images/249.png)
选择**Active Directory Certificate Service**
![](/images/250.png)
![](/images/251.png)
![](/images/252.png)
![](/images/253.png)
![](/images/254.png)
选择**Network Device Enrollment Service**，取消勾选**Certificate Authority**
![](/images/255.png)
![](/images/256.png)
确保以下组件已被勾选：

		
		Web Server > Security > Request Filtering

		Web Server > Application Development > ASP.NET 3.5

			Installing ASP.NET 3.5 installs .NET Framework 3.5. When installing .NET Framework 3.5, install both the core .NET Framework 3.5 feature and HTTP Activation.

		Web Server > Application Development > ASP.NET 4.5

			Installing ASP.NET 4.5 installs .NET Framework 4.5. When installing .NET Framework 4.5, install the core .NET Framework 4.5 feature, ASP.NET 4.5, and the WCF Services > HTTP Activation feature.

		Management Tools > IIS 6 Management Compatibility > IIS 6 Metabase Compatibility

		Management Tools > IIS 6 Management Compatibility > IIS 6 WMI Compatibility

		On the server, add the NDES service account as a member of the local IIS_IUSR group.

![](/images/257.png)
![](/images/258.png)

2. 在提升权限的CMD窗口中，输入以下命令，为NDES service account设置SPN。

		setspn -s http/<DNS name of NDES Server> <Domain name>\<NDES Service account name>

# 配置NDES

## 打开AD CS配置向导。

![](/images/259.png)

![](/images/260.png)
![](/images/261.png)
![](/images/262.png)
![](/images/263.png)
![](/images/264.png)
![](/images/265.png)
![](/images/266.png)
![](/images/267.png)

## 修改NDES服务器注册表键值

1. 查看证书模板的**Properties** -> **Request Handling** -> **Purpose**，可以看到是**Encryption**。

![](/images/268.png)

2. 查看证书模板的**Properties** -> **General** -> **Template name**，可以看到是**NDESCertificate**。

![](/images/269.png)

2. 打开注册表编辑器，找到以下位置：

		HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP\

3. 修改注册表前，可以看到以下键值。

![](/images/270.png)

4. 由于证书模板的**Purpose**是**Encryption**，因此，将**EncryptionTemplate**的值修改为证书模板的**Template name**，即**NDESCertificate**。

![](/images/271.png)

5. 修改以下注册表键值，可以使得NDES服务器接收长URL请求。

![](/images/272.png)

6. 打开IIS manager, 选择** Default Web Site > Request Filtering > Edit Feature Setting**. 修改**Maximum URL length** 和 **Maximum query string** 为 **65534**。

![](/images/273.png)

7. 重启NDES服务器。
8. 打开浏览器，访问`http://*FQDN*/certsrv/mscep/mscep.dll`，应该可以看到以下页面。

![](/images/274.png)

## 配置IIS服务

1. 在NDES服务器上，打开证书管理器，选择请求服务器认证证书。

![](/images/275.png)
![](/images/276.png)
![](/images/277.png)
![](/images/278.png)
![](/images/279.png)

2. 打开IIS管理器，选择**Binding**。

![](/images/280.png)

3. 添加SSL服务器证书。

![](/images/281.png)
![](/images/282.png)

> **Note**

>If the NDES server uses an external and internal name for a single network address, then the server authentication certificate must have:
>
- A **Subject Name** with an external public server name
- A S**ubject Alternative Name** that includes the internal server name

4. 申请客户端认证证书，用于**Intune Certificate Connector**。由于之前申请的服务器认证证书的**Enhanced Key Usage**同时支持**Client Authentication** 和 **Server Authentication**，因此可以使用同一张证书，不需要再次申请。

![](/images/283.png)



