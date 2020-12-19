---
title: 如何用System帐号运行程序
date: 2020-12-19 10:53:29
tags:
- Intune
---

某些情况下，需要用System账号来运行程序。以下针对CMD为例，通过Psexec来使用SYSTEM账号运行cmd.exe。

1. 下载[PsExec](https://docs.microsoft.com/en-us/sysinternals/downloads/psexec)。
2. 将下载的**PsTools.zip**压缩包解压后，拷贝文件**PsExec.exe**或者**PsExec64.exe**到**C:\Windows\System32**目录。
3. 以管理员身份运行CMD
4. 输入以下命令后，会打开一个新的以SYSTEM账号运行的命令行窗口

    `PsExec.exe -i -d -s cmd.exe`

5. 打开任务管理器，查看进程cmd.exe的运行账号为SYSTEM。

![](/images/468.png)
