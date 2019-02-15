---
title: "问题：设备注册到Intune时提示MFA注册"
date: 2019-02-15 13:30:24
tags:
- Intune
categories:
- 企业产品
---
# 问题

没有配置MFA的策略，但是在将设备通过Company Portal或者Settings应用注册到Intune过程中，提示需要注册MFA。


# 问题描述

通过Company Portal或者Settings应用注册到Intune时，输入用户名和密码以后，提示注册MFA。

![](/images/183.png)
<!-- more -->
![](/images/184.png)



# 问题分析

在客户端电脑上，查看设备注册状态，**发现设备注册到MAM服务器**。

![](/images/185.png)

在Azure AD门户中，查看Automatic Enrollment的配置，发现用户所在组配置了MAM Enrollment。

![](/images/186.png)

# 解决方法

在Azure AD门户中，打开Automatic Enrollment的配置，将**MAM User Scope**选择为**None**。

![](/images/187.png)



