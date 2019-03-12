---
title: SCEP证书(三)：安装和配置Intune Certificate Connector
date: 2019-03-12 15:31:09
tags:
- Intune
categories:
- 企业产品
---
1. 登陆Intune门户，下载**Intune Certificate Connector**安装文件。

![](/images/284.png)

<!-- more -->

2. 打开**Server Manager**，关闭**IE Enhanced Security Configuration**选项

![](/images/285.png)
3. 在NDES服务器上，双击安装文件**NDESConnectorSetup.exe**，开始安装。

![](/images/286.png)
![](/images/287.png)
![](/images/288.png)
![](/images/289.png)
![](/images/290.png)
![](/images/291.png)
![](/images/292.png)
![](/images/293.png)
![](/images/294.png)

4. 用Azure AD全局管理员登陆，该账号必须有Intune License。


![](/images/295.png)
![](/images/296.png)
![](/images/297.png)

5. 输入之前创建的企业AD账号zurelab\ndes。

![](/images/298.png)

> **提示**
> 关闭UI后，可以通过**C:\Program Files\Microsoft Intune\NDESConnectorUI\NDESConnectorUI.exe**，重新打开UI。

6. 打开**Service.msc**,重新启动**Intune Connector Service**。
7. 在浏览器中，输入URL: `http://<FQDN_of_your_NDES_server>/certsrv/mscep/mscep.dll`,正常情况下，应该能看到403错误页面。

![](/images/299.png)
