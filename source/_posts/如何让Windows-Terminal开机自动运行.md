---
title: 如何让Windows Terminal开机自动运行
date: 2020-10-31 20:31:15
tags:
- Windows
---

由于经常需要使用命令行工具，所以十分依赖于**Windows Terminal**。但是，每次进入Windows系统，都要手动点击运行**Windows Terminal**，觉得还是有点麻烦。并且，如果要用管理员来运行，还要右键点击后，选择以管理员身份运行。

虽然在设置中，可以配置Windows Terminal随机启动，但是却无法指定用管理员身份运行。所以，想到通过创建快捷方式，并且放到启动目录的方式来解决问题。

# 方法一

## 创建计划任务

1. 打开计划任务程序。
2. 创建新的任务。
3. 在**常规**中，选择**使用最高权限运行**。
![](/images/424.png)

4. 在**触发器**中，**开始任务**选择**登录时**。
![](/images/425.png)

5. 在**操作**中，配置参数如下：
    
    **程序或脚本**："C:\Program Files\WindowsApps\Microsoft.WindowsTerminal_1.3.2651.0_x64__8wekyb3d8bbwe\wt.exe"
    
    **参数**：-M //设置该参数可以将Windows Terminal打开后窗口最大化

    **起始于**："C:\Program Files\WindowsApps\Microsoft.WindowsTerminal_1.3.2651.0_x64__8wekyb3d8bbwe"

![](/images/426.png)

====================================================================

**注意**

通过测试，**方法二无法成功让Windows Termianl自动运行**。

如果在快捷方式的文件属性中配置了以管理员身份运行，在用户登录的后，该快捷方式并没有自动运行。但是，如果取消配置以管理员身份运行，在用户登录的后，该快捷方式可以自动运行，并打开Windows Terminal应用。

如果手动点击该快捷方式，可以以管理员身份运行Windows Terminal。

====================================================================

# 方法二
## 创建快捷方式

1. 打开文件资源管理器，访问目录C:\Program Files\WindowsApps\Microsoft.WindowsTerminal_1.3.2651.0_x64__8wekyb3d8bbwe。

2. 右键点击**wt.exe**，选择**发送到**-**桌面快捷方式**。

3. 右键点击桌面上的**wt.exe-快捷方式**，选择**属性**，然后选择**高级**。

![](/images/421.png)

4. 选择**用管理员身份运行**。

![](/images/422.png)

## 复制快捷方式到启动目录

1. 在键盘上同时按下**Win + R**，打开运行窗口。
   
2. 输入**shell:startup**后，按回车后，进入启动目录。

![](/images/423.png)

3. 将快捷方式**wt.exe-快捷方式**复制到启动目录下。

重启电脑后，登录Windows系统后，Window Terminal就会自动以管理员身份运行。