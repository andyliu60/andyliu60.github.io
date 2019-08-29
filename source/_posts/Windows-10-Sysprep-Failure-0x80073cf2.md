---
title: 'Windows 10 Sysprep Failure: 0x80073cf2'
date: 2019-08-29 16:28:38
tags:
- SCVMM
categories:
- 企业产品

---

# 问题描述

在Windows 10操作系统中，运行Sysprep失败。

![](/images/406.png)

![](/images/407.png)



# 问题原因

查快日志发现，由于之前安装了新的系统语言，连带安装了Microsoft.LanguageExperiencePacken-US。导致Sysprep失败。

![](/images/408.png)



# 解决方法

在Powershell中，运行以下命令删除Microsoft.LanguageExperiencePacken-US后，Sysprep成功。

`Get-AppxPackage -Name Microsoft.LanguageExperiencePacken-US | Remove-AppxPackage`



创建