---
title: SCVMM-安装篇
date: 2019-06-20 14:11:40
tags:
- SCVMM
categories:
- 企业产品
---
本文主要介绍如何一步步安装System Center Virtual Machine Manager 2019。

# 安装环境

服务器：虚拟机

CPU: 4个虚拟处理器

内存：4GB(动态)

硬盘：40GB(可扩展)

操作系统：Windows Server 2016
<!-- more -->

# 准备工作

## 创建账号和组


- **Domain\scvmmadmin**	- SCVMM Service Account account
- **Domain\scvmmadmins** - SCVMM Administrators Global Security Group
- **Domain\scvmmsql** -  SQL service account

## 安装Windows ADK for Windows 10 1093

下载地址：https://docs.microsoft.com/en-us/windows-hardware/get-started/adk-install

安装**Deployment Tools**组件。

![](/images/307.png)

## 安装Windows PE

下载地址：https://docs.microsoft.com/en-us/windows-hardware/get-started/adk-install

安装Windows PE。

![](/images/308.png)

## 安装SQL 2016 Command Line Utilities

下载[Microsoft® ODBC Driver 11 for SQL Server®](https://www.microsoft.com/en-us/download/details.aspx?id=53339)和[SQL 2016 Command Line Utilities](https://www.microsoft.com/en-us/download/confirmation.aspx?id=52676)

文件名：**msodbcsql**
文件名：**MsSqlCmdLnUtils**

先安装**Microsoft® ODBC Driver 11 for SQL Server®**，后安装**SQL 2016 Command Line Utilities**。

# 安装SQL Server 2016

![](/images/309.png)
![](/images/310.png)
![](/images/311.png)
![](/images/312.png)
![](/images/313.png)
![](/images/314.png)
![](/images/315.png)
![](/images/316.png)
![](/images/317.png)
![](/images/318.png)
![](/images/319.png)


# 安装SCVMM

![](/images/320.png)
![](/images/321.png)
![](/images/322.png)
![](/images/323.png)
![](/images/324.png)
![](/images/325.png)
![](/images/326.png)
![](/images/327.png)
![](/images/328.png)
![](/images/329.png)
![](/images/330.png)
![](/images/331.png)
![](/images/332.png)
![](/images/333.png)
![](/images/334.png)
![](/images/335.png)