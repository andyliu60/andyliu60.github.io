---
title: Kiosk模式下运行Kiosk Browser
date: 2019-02-11 12:20:27
tags:
- Intune
categories:
- 企业产品
---
# 配置和推送Kiosk Browser应用

1. 在Intune门户中，选择**Client apps > Apps**，搜索关键字"Kiosk"，查找**Kiosk Browser**应用。
<!-- more -->
![](/images/128.png)


2. 选择**Kiosk Browser**，选择**Assignment**.

3. 选择**Add group**，选择**Assignment type**为**Required**，并选择设备组。

![](/images/129.png)

4. 保存配置

# 配置和推送Kiosk配置文件

1. 在Intune门户中，选择**Device configuration - Profiles**，选择**Create profile**。

2. 选择**Profile type**为**Kiosk**。

![](/images/130.png)

3. 配置**Kiosk Browser Settings**。

![](/images/131.png)

# 客户端查看结果

1. 用Azure AD账号登陆并同步设备，并确认**Kiosk Browser**已经成功安装。
2. 重启设备。

![](/images/132.png)