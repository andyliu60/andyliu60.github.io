---
title: >-
  SCVMM:Error(2912) An internal error has occurred trying to contact the
  'hv01.contoso.com' server
date: 2019-08-13 15:01:26
tags:
- SCVMM
categories:
- 企业产品
---
# 问题描述

在VMM控制台中，刷新主机失败。

![](/images/376.png)

# 问题原因

Hyper-V主机的系统版本太低。

Hyper-V主机操作系统版本：**14393.1198**


# 解决方法

在Hyper-V主机安装最新的操作系统更新包，更新至版本：**14393.3115**
