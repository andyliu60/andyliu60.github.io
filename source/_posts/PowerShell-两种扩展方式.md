---
title: 'PowerShell:两种扩展方式'
date: 2019-07-17 10:20:04
tags:
- PowerShell
categories:
- 企业产品
---
PowerShell支持两种扩展方式：**Modules** 和**Snap-ins**。

# Snap-ins

Snap-ins在PowerShell中的名称是**PSSnapin**。**PSSnapin**通常由DLL文件和XML文件组成，其中XML文件包含配置和帮助文本。

在PowerShell中，**PSSnapin**必须要安装和注册后，才能正常使用。

 	get-pssnapin -registered      //查看已安装和注册的PSSnapins
 	add-pssnapin sqlservercmdletsnapin100        //加载PSSnapins

# Modules

在PowerShell中，Modules不需要注册。PowerShell会通过特定的路径自动查找Modules。当用户查询Modules的帮助信息，或者使用Modules中的命令时，PowerShell会自动加载模块。

因此，模块可以被PowerSehll自动发现和自动加载。

环境变量**PSModulePath**定义了模块的存储路径。

	PS C:\> get-content env:psmodulepath
	C:\Users\Administrator\Documents\WindowsPowerShell\Modules;C:\Windows\system32\WindowsPowerShell\v1.0\Modules\

常用命令：

	Get-Module
	Import-Module
