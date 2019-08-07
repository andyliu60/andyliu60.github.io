---
title: >-
  SCVMM:Error (20406) VMM could not enumerate instances of class
  Msvm_EthernetDeviceSAPImplementation on the server hv-node01.contoso.com
date: 2019-08-07 14:49:09
tags:
- SCVMM
categories:
- 企业产品
---

# 问题描述

在VMM控制台中，刷新主机报错。

![](/images/375.png)

# 问题原因

Hyper-V主机的系统时间与VMM服务器不一致。


# 解决方法

调整Hyper-V主机的系统时间，确保其与VMM服务器的时间相同。

