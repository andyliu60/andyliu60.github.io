---
title: "Intune Enrollment: Windows BYOD Enrollment"
date: 2019-02-15 09:19:48
tags:
- Intune
categories:
- 企业产品
---
BYOD Enrollment主要适用于用户通过在自己**私人**的手机、平板和电脑上安装**Company Portal**，将设备注册到Intune。

对于Windows 10设备来说，除了可以通过**Company Portal**注册到Intune以外，也可以通过**Settings**应用注册。

# 通过Company Portal注册

1. 从微软商店中，下载并安装**Company Portal**应用。

![](/images/167.png)

<!-- more -->

2. 打开**Company Portal**，输入用户名和密码。

![](/images/168.png)
![](/images/169.png)

3. 选择Yes。

![](/images/170.png)

4. 选择Done。

![](/images/171.png)

5. 选择设备类别（Intune管理员可以在Intune门户中创建设备类别）。

![](/images/172.png)

6. 设备注册成功，进入**Company Poral**首页。

![](/images/173.png)

# 通过Settings注册

1. 打开**Settings**应用，选择**Accounts - Access work or school**。

![](/images/174.png)

2. 点击Connect，输入用户名和密码。

![](/images/175.png)
![](/images/176.png)

3. 点击Done，完成注册。

![](/images/177.png)
![](/images/178.png)

# 查看设备注册状态

1. 在Intune门户中，可以看到设备已经注册到Azure Active Directory和Intune。

2. 选择Devices > Azure AD devices,可以看到设备在Azure AD中的**Join Type**是**Azure AD registered**。

![](/images/179.png)

3. 选择Devices > All devices，可以看到设备的**Ownership**是**Personal**。

![](/images/180.png)

4. 在客户端电脑上，打开**Settings**应用，选择**Accounts - Access work or school**，选择账号，并点击**Info**。

![](/images/181.png)

5. 可以看到设备已经同步成功。

![](/images/182.png)
