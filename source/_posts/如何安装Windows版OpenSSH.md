---
title: 如何安装Windows版OpenSSH
date: 2019-07-08 14:44:16
tags:
- Windows
categories:
- 企业产品
---
在Windows 10 1809和Windows Server 2019或者以上的操作系统中，默认已经包含OpenSSH客户端和服务器功能，可以在Settings - Apps中启用。

本文主要介绍如何在Windows Server 2016上安装OpenSSH。

# 安装OpenSSH

1. 下载[OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/releases)，通常下载的文件名为**OpenSSH-Win64.zip**。
2. 解压文件**OpenSSH-Win64.zip**，并将其保存到**C:\Program Files\**。
![](/images/362.png)
<!-- more -->
3. 用管理员权限打开PowerShell，并运行以下命令安装OpenSSH。

	.\install-sshd.ps1
![](/images/363.png)
4. 打开服务控制面板，将OpenSSH的服务设置为自动启动，并启动OpenSSH服务。
![](/images/364.png)

# 添加环境变量

1. 打开**系统**属性，在**高级**中，选择**环境变量**。

![](/images/365.png)

2. 选择**路径**，点击**编辑**。

![](/images/366.png)

3. 点击**添加**，输入OpenSSH的安装路径。

![](/images/367.png)

# 添加防火墙策略

添加防火墙策略，运行22端口的访问。

![](/images/368.png)
![](/images/369.png)
![](/images/370.png)
![](/images/371.png)
![](/images/372.png)

