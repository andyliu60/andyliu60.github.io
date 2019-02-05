---
title: 'Intune Enrollment: iOS Apple Configurator'
date: 2019-02-05 20:54:35
tags:
- Intune
categories:
- 企业产品
---
Intune支持用Apple Configurator将iOS设备注册到Intune服务。如果采用这种方式，需要将iOS设备通过USB线连接到Mac电脑。

用Apple Configurator注册设备共有两种方式：

* Setup Assistant Enrollment - 需要将设备恢复出厂设置
* Direct enrollment - 不需要将设备恢复出厂设置，但是只支持no user affinity

# 创建Apple Configurator Profile

1. 在Intune门户中，选择Device enrollment > Apple enrollment > Apple Configurator > Profiles > Create.

![](/images/75.png)

2. 输入名称，选择Enroll with user affinity，设置“Authenticate with Company Portal instead of Apple Setup Assistant”为Yes

![](/images/76.png)

3. 在Azure AD中创建动态组，规则参数enrollmentProfileName设置为Equles配置文件名称。

![](/images/77.png)

<!-- more -->  

# 上传设备序列号

1. 在iOS设备上，打开**设置**，选择**通用 - 关于**，获取iOS设备序列号

2. 创建csv文件,文件内容如下

F7TLWCLBX196,device details

3. 在Intune门户中，选择Device enrollment > Apple enrollment > Apple Configurator > Devices, 选择Profile, 并上传csv文件。

![](/images/78.png)

4. 上传完成后，可以看到设备的序列号等信息

![](/images/79.png)

5. 在Profile的Devices中，可以看到已经分配该配置文件的设备。

![](/images/80.png)

6. 导出Apple Configurator Profile，拷贝Profile URL

![](/images/81.png)


# 用Apple Configurator配置iOS设备

1. 将iOS设备恢复出厂设置。
2. 用USB线将iOS设备连接到Mac电脑
3. 打开Apple Configurator软件，打开**偏好设置**
4. 选择**服务器**
![](/images/82.png)
5. 点击"+"创建服务器
![](/images/83.png)
6. 输入名称，在“主机名或URL”输入导出的Profile URL
![](/images/84.png)
7. 创建完成后，可以看到获取到的证书
![](/images/85.png)
![](/images/86.png)
8. 在Apple Configurator主界面中，选中iPhone设备，并选择“准备”
![](/images/87.png)
9. 选择“手动配置”，点击下一步
![](/images/88.png)
10. 选择服务器“Intune”，点击下一步
![](/images/89.png)
11. 选择“新建组织”，点击下一步
![](/images/90.png)
12. 点击“跳过”
![](/images/91.png)
13. 输入组织名称，点击下一步
![](/images/92.png)
14. 选择“生成新的监督身份”，点击下一步
![](/images/93.png)
15. 配置iOS设置助理，点击“准备”
![](/images/94.png)

# 完成iPhone设置助理

1. 打开iPhone，选择语言为简体中文
![](/images/95.png)
2. 选择国家和地区
![](/images/96.png)
3. 选择键盘
![](/images/97.png)
4. 选择应用配置
![](/images/98.png)
![](/images/99.png)
5. 创建密码
![](/images/100.png)
6. 启用定位服务
![](/images/101.png)
7. 开始使用
![](/images/102.png)

接下来，需要安装Company Portal,打开Company Portal后，输入用户名和密码登陆，否则，设备在Intune中,Compliance状态显示为Not Evaluated.

![](/images/103.png)

8. 输入Apple ID, 登陆iTunes

![](/images/104.png)
![](/images/105.png)

9. 打开Company Portal, 输入Azure AD帐号和密码

![](/images/106.png)
![](/images/107.png)
![](/images/108.png)

10. 选择“开始”，完成设备管理

![](/images/109.png)
![](/images/110.png)
![](/images/111.png)
![](/images/112.png)
![](/images/113.png)

在Intune门户中查看，可以看到设备已经显示为Compliant.

![](/images/114.png)