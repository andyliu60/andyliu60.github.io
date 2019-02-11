---
title: Intune-自动启用BitLocker加密
date: 2019-02-11 09:28:07
tags:
- Intune
categories:
- 企业产品
---
通过Intune，可以为Windows设备配置BitLocker参数，并且自动启用BitLocker。

在Intune门户中， BitLocker策略的路径如下：

		Microsoft Intune > Device configuration - Profiles > Create profile > Endpoint protection

<!-- more -->
BitLocker策略的设置主要包括以下几部分：


- Windows Settings —— 启用BitLocker设备加密。
- BitLocker base settings —— 通用BitLocker加密设置，适用于所有驱动器类型。
- BitLocker OS drive settings —— 操作系统所在驱动器的加密设置，如C盘。
- BitLocker fixed data-drive settings —— 数据驱动器的加密设置，如D, E盘等。
- BitLocker removable data-drive settings —— 可移动磁盘的加密设置

# 系统盘启用BitLocker加密

1. 登陆Intune门户，选择**Microsoft Intune > Device configuration - Profiles**，点击**“Create profile”**创建策略，输入名称，选择**Platform**为**“Windows 10 and later”**，选择**“Profile type”**为**"Endpoint protection"**。
![](/images/125.png)

2. 选择**“Windows Encryption”**，打开BitLocker设置相关的页面。

3. 在**"Windows Settings"**中，设置**“Encrypt devices”**为**“Require”**。

4. 在**“BitLocker base settings”**中，设置以下参数。

	Warning for other disk encryption: **Block**
	
	Allow standard users to enable encryption during Azure AD Join: **Allow**
	
	Configure encryption methods: **Enable**
	
	Encryption for operating system drives: **XTS-AES-256-bit**

![](/images/126.png)

5. 将策略分配给设备组。

6. 在客户端电脑上，用管理员权限打开CMD，并输入以下命令。该命令可以查看加密的状态和参数。

		manage-bde -status c:

![](/images/127.png)
