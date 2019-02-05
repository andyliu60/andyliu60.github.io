---
title: 'Intune Retire, Wipe, Fresh Start and AutoPilot Reset'
date: 2019-02-05 14:52:29
tags:
- Intune
categories:
- 企业产品
---
# Retire

**Retire**用于删除设备上的公司数据，保留个人数据。

公司数据包括企业应用数据，设置，配置文件等。

**Retire不适用于加入Azure AD的Windows 10 设备。**

**Retire**比较适合用于个人设备。

# Wipe

**Wipe**将设备恢复出厂设置。

执行Wipe操作后，设备立刻自动重启，并进行重置。

![](/images/65.png)

重置完成后，需要重新经历整个OOBE过程。

![](/images/66.png)

对于Windows 10 1709或以上版本的设备，还可以选择**"Retain enrollment state and user account"**，该选项将保留该设备在Intune的注册状态。

![](/images/67.png)

重置完成后，用户可以直接输入用户名和密码登录。

![](/images/68.png)

<!-- more -->  

# AutoPilot Reset

**AutoPilot Reset**会删除所有的数据和配置，保留设备在Azure AD和Intune中的信息。要执行该操作，必须：

- 设备加入Azure AD
- 设备被Intune管理
- 配置**“Enrollment status page”**

执行AutoPilot Reset的操作后，客户端设备会收到提示信息，约45分钟后设备就会自动重启，并开始重置设置。

![](/images/74.png)

**注：重置完成后，设备使用原有的主机名**

![](/images/69.png)
![](/images/70.png)

重置完成后，设备会自动进行配置，不需要用户进行干预。

![](/images/71.png)
![](/images/72.png)

最后，用户只需要输入用户名和密码登录系统。
![](/images/73.png)


# Fresh Start

**Fresh Start**可以删除OEM设备上预装的Win32程序。如果选择“Retain user data on this device”，设备将保留Azure AD和Intune注册信息。否则， 设备将被重置为OOBE状态。 



