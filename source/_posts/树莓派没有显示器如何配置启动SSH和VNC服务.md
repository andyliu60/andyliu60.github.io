---
title: 树莓派没有显示器如何配置启动SSH和VNC服务
date: 2020-11-08 08:42:39
tags:
- RaspberryPi
---

最近刚入手一台树莓派4B，但是，由于树莓派从4代开始，改用Micro HDMI作为显示器的输出口，家中没有Micro HDMI - Standard HDMI的连接线，所以，无法连接显示器，完成初始配置。

于是，想通过SSH和VNC来远程访问树莓派，但是，这两个服务默认都没有自动开启。

通过在网上搜索别人的经验，发现只需要在SD卡的Boot分区中创建空白的ssh文件，就可以让树莓派开机自动启动SSH服务。

# 开启SSH服务

1. 将烧录好Raspbian系统的SD卡插入电脑。
2. 在boot分区中，用记事本创建一个新文件，文件名为ssh，注意需要将后缀.txt删除。

![](/images/427.png)

3. 把SD卡插入树莓派，通电启动后，SSH服务会自动开启。


# 开启VNC服务

1. 通过SSH，远程访问树莓派。
2. 输入**sudo raspi-config**, 打开树莓派配置工具。
3. 选择**Interface Options**。

![](/images/428.png)

4. 选择**P3 VNC**。

![](/images/429.png)

5. 选择**Yes**，开启VNC服务。

![](/images/430.png)