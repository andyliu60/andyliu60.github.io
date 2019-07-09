---
title: 'PowerShell: 如何查找命令'
date: 2019-07-09 16:36:20
tags:
- PowerShell
categories:
- 企业产品
---
# 方法一：使用**Get-Help**查找命令

PowerShell的help系统中包含所有命令的说明文档，因此，可以通过**Get-Help**命令查找相关命令。实际上，**Get-Help**并不是直接搜索命令，而是搜索关于命令的主题。

例子：


	Get-Help -Name *log*
	Get-Help -Name *event*

![](/images/373.png)


# 方法二：使用**Get-Command**查找命令

与**Get-Help**搜索关于命令的主题不同，**Get-Command**可以直接搜索命令。

例子：


	Get-Command -Name *log*
	Get-Command -Noun *log*
	Get-Command -Verb Get
	Get-Command -Name *log* -CommandType Cmdlet

![](/images/374.png)

