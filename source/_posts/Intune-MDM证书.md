---
title: Intune MDM证书
date: 2019-02-12 16:36:58
tags:
- Intune
categories:
- 企业产品
---
设备注册Intune成功以后，或获取到一张由Intune颁发的MDM证书。设备利用这张证书与Intune通讯。

<!-- more -->

# Windows

在Windows 10设备上，打开MMC管理工具，添加**计算机证书**管理组件，可以在**Certificates(Local Computer) - Personal - Certificates**中，查看该MDM证书。

![](/images/150.png)

**该证书的颁发者为：Microsoft Intune MDM Device CA, 有效期为1年。**

![](/images/151.png)

![](/images/152.png)