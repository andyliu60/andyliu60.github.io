---
title: Wi-Fi密码转换成二维码
date: 2020-02-14 18:17:55
tags:
- iOS
---

# 生成二维码

下载并安装[qrencode](https://packages.debian.org/stable/qrencode).

运行以下命令：

```
qrencode -o wifi.png "WIFI:T:WPA;S:<SSID>;P:<PASSWORD>;;"
```
将<SSID\> 替换成Wi-Fi网络的名称，将<PASSWORD\>替换成Wi-Fi网络的密码。

如果密码中包含“:”，需要用反斜杠进行转义。例如：

```
"WIFI:T:WPA;S:<SSID>;P:pass\:word;;"
```

# 扫描二维码

在iPhone手机上，打开相机，直接扫码二维码。

  ![](/images/412.png)

在Android手机上，打开WiFi设置，选择需要连接的Wi-Fi网络，扫码二维码。

 ![](/images/413.png)
 ![](/images/414.png)






