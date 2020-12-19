---
title: 如何访问不加入域的Hyper-V服务器
date: 2020-12-19 15:47:25
tags:
- Windows
---

# Hyper-V服务器

1. 打开PowerShell，启用WinRM。

    `Enable-PSRemoting`

2. 启用并配置CredSSP
   
   `Enable-WSManCredSSP -Role server`


# Windows客户机

1. 打开PowerShell, 启用WinRM
   
   `Enable-PSRemoting`

2. 配置受信任的主机
   
   `Set-Item WSMan:\localhost\Client\TrustedHosts -Value *`

3. 启用并配置CredSSP
   
   `Enable-WSManCredSSP -Role client -DelegateComputer *`

4. 打开本地组策略管理器，选择**Computer Configuration - Administrative Templates - System - Credential Delegation**

![](/images/469.png)

5. 选择**Allow delegating fresh credentials with NTLM-only server authentication**
![](/images/470.png)

6. 输入**wsman/***
![](/images/471.png)