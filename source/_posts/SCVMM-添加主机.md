---
title: 'SCVMM: 添加主机'
date: 2019-06-24 13:47:21
tags:
- SCVMM
categories:
- 企业产品
---
本文主要介绍如何加Hyper-V主机添加到SCVMM中，从而对其进行管理。

![](/images/336.png)
<!-- more -->
![](/images/337.png)
![](/images/338.png)
![](/images/339.png)
![](/images/340.png)
![](/images/341.png)
![](/images/342.png)
![](/images/343.png)
![](/images/344.png)

# 出现的问题

1. SCVMM Service account和 Run As account 不能使用同一个账号。否则，添加主机会出错。

![](/images/345.png)

2. 安装SCVMM Server是，使用域账号为SCVMM Service Accoun, 添加主机出现以下错误。重装SCVMM，并使用本地账号为SCVMM Service Account，问题解决。

![](/images/346.png)