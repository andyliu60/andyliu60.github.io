---
title: 'SCCM:使用PXE的方式安装操作系统'
date: 2019-07-03 10:53:40
tags:
- SCCM
categories:
- 企业产品
---
# Windows ADK for Windows  10

Windows ADK包含了一整套的工具，用于配置和安装Windows操作系统。需要安装的组件包括：

- **Deployment Tools**
- **User State Migration Tool (USMT)**

![](/images/361.png)
<!-- more -->

下载[Windows ADK for Windows 10](https://docs.microsoft.com/en-us/windows-hardware/get-started/adk-install)

Windows ADK需要安装在每一台SCCM站点服务器上。

# Windows PE

Windows PE是一个小型的Windows操作系统，用于启动计算机，并安装和部署Windows操作系统。

下载[Windows PE](https://docs.microsoft.com/en-us/windows-hardware/get-started/adk-install)

>Important
> 
> Starting with Windows 10 version 1809, Windows PE is a separate installer. Otherwise there's no functional difference.

# DHCP服务器

通过PXE方式安装和部署Windows操作系统，必须要准备一台DHCP服务器。

# Boot Image

Boot Image用于启动计算机进入**Windows Preinstallation Environment**(WinPE)。在SCCM中，Boot Image就是Windows PE。

# OS Image

OS Image以 Windows Imaging (WIM)的格式存储在SCCM。

在操作系统的ISO文件中，可以在以下路径找到默认的Image文件。

	\Sources\install.wim

## 添加OS Image

## 发布OS Image到DP

# DP启用PXE

![](/images/362.png)

# Task Squences

