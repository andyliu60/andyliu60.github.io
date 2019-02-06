---
title: Windows AutoPilot 概述
date: 2019-02-06 11:27:58
tags:
- Intune
categories:
- 企业产品
---
Windows AutoPilot是一种新的Windows设备部署方式，只适用于Windows10 1703或者以上的版本。

当企业购买了新的电脑后，在传统的IT管理方式中，IT管理员需要为电脑重新安装企业定制的镜像，并且安装各种企业软件，加入公司域，并推送组策略等。然后，IT管理员再将电脑分发给员工。

通过Windows AutoPilot的部署方式，企业购买的新电脑将直接发送给员工。IT管理员只需要利用Intune将配置文件远程分配给每台电脑，而员工则只需要将电脑开机，并连接网络，电脑自动完成配置以后，员工输入账号和密码就可以登录使用。

简单来说，Windows AutoPilot主要分为三步：

**1. 设备注册**

设备注册需要设备供应商或者IT管理员将硬件ID上传到Windows AutoPilot Deployment service.

可以通过以下途径上传硬件ID:

- Microsoft Intune
 
- Microsoft Store for Business 

- Microsoft 365 Business & Office 365 Admin 

- Partner Center

其中，设备供应商可以通过Partner Center上传硬件ID。

**2.  创建和分发配置文件**

通过创建配置文件，可以自定义Windows系统的OOBE过程，改善用户体验。

**3. 开机使用**

员工开机后，只需要输入账号和密码，就可以立即使用电脑。


**Windows AutoPilot可以为企业带来以下好处：**

1. 自动将设备加入Azure AD或者企业AD。
2. 自动将设备注册到Intune。
3. 限制Azure AD用户拥有本地管理员权限。
4. 定制OOBE的内容
5. 为企业现有的Windows 7和Windows 8.1设备部署Windows 10系统。
6. User-Driven模式
7. Self-deploying模式，适用于公用的电脑，如Kiosk等
8. Windows AutoPilot Reset

