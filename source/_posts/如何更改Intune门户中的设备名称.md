---
title: 如何更改Intune门户中的设备名称
date: 2019-02-08 14:34:01
tags:
- Intune
categories:
- 企业产品
---
根据[文档](https://docs.microsoft.com/en-us/intune-user-help/rename-your-device-cpapp)介绍，用户可以通过Intune Company Portal for Windows app或者 Intune Company Portal website重命名设备。但是，该操作只是设置了一个别名，以便于用户区分自己的设备，并不会真的更改设备名或者主机名。**因此，该通过该重命名操作更改后的设备名称，并不会同步并更新Intune门户的设备名。**

# Windows

在Intune门户中，在**Devices > All devices**页面中，设备的名称通常就是计算机的主机名。管理员无法在该界面中直接更改设备名称。但是，可以通过以下方式更改：


<!-- more -->

1. 登录到Windows设备，更改计算机名称。可以在系统属性中更改计算机名称，或者使用PowerShell命令。

		Rename-Computer -NewName “Workstation001”

2. 打开**Settings**应用，在**Access work and school**界面中，手动触发与Intune的同步操作。或者，也可以等系统自动同步。

3. 在Intune门户中，在**Devices > All devices**和**Devices > Azure AD devices**页面中的设备名称都会自动更新为新设置的主机名。


# iOS

在Intune门户中，选择**Devices > All devices > <Choose the device> > More > Rename device(Supervised only)**, 输入新的设备名称。

![](/images/123.png)
![](/images/124.png)

# Android

在Android设备中直接更改设备名称。