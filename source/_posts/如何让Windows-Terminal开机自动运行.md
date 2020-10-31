---
title: 如何让Windows Terminal开机自动运行
date: 2020-10-31 20:31:15
tags:
- Windows
---

由于经常需要使用命令行工具，所以十分依赖于**Windows Terminal**。但是，每次进入Windows系统，都要手动点击运行**Windows Terminal**，觉得还是有点麻烦。并且，如果要用管理员来运行，还要右键点击后，选择以管理员身份运行。

虽然在设置中，可以配置Windows Terminal随机启动，但是却无法指定用管理员身份运行。所以，想到通过创建快捷方式，并且放到启动目录的方式来解决问题。

# 创建快捷方式

1. 打开文件资源管理器，访问目录C:\Program Files\WindowsApps\Microsoft.WindowsTerminal_1.3.2651.0_x64__8wekyb3d8bbwe。

2. 右键点击**wt.exe**，选择**发送到**-**桌面快捷方式**。

3. 右键点击桌面上的**wt.exe-快捷方式**，选择**属性**，然后选择**高级**。

![](/images/421.png)

4. 选择**用管理员身份运行**。

![](/images/422.png)

# 复制快捷方式到启动目录

1. 在键盘上同时按下**Win + R**，打开运行窗口。
   
2. 输入**shell:startup**后，按回车后，进入启动目录。

![](/images/423.png)

3. 将快捷方式**wt.exe-快捷方式**复制到启动目录下。

重启电脑后，登录Windows系统后，Window Terminal就会自动以管理员身份运行。