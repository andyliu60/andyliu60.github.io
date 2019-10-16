---
title: 在不加入域的工作机上安装SCVMM Console
date: 2019-10-16 08:47:49
tags:
- SCVMM
categories:
- 企业产品
---



如果在一台不加入公司域的工作机上安装SCVMM Console，会出现以下报错界面：

![](../images/411.png)

根据报错内容，要求工作机必须加入公司域以后，并且以域账号登录该工作机，才能开始安装SCVMM Console。

**解决方法：**

用管理员权限打开CMD命令行，输入以下命令安装。

 `setup.exe /client /i /IACCEPTSCEULA`





