---
title: Intune PowerShell scripts-设置时区
date: 2019-02-08 08:54:22
tags:
- Intune
categories:
- 企业产品
---
# 创建PowerShell脚本

		Set-TimeZone -Name "China Standard Time"

<!-- more -->

# 上传脚本到Intune

1. 在Intune门户中，选择**Device configuration > PowerShell Scripts > Add**
2. 输入策略名称和描述，上传脚本。脚本的大小必须小于200 KB (ASCII) or 100 KB (Unicode)
3. 选择脚本是否以当前登陆用户运行， 选择**"No"**
![](/images/115.png)
4. 保存策略
5. 将策略分配给用户组
![](/images/116.png)

# 查看脚本运行结果

在Intune门户中，可以分别对设备和用户查看脚本的运行结果。

![](/images/117.png)
![](/images/118.png)

# 如何确认**Intune Management Extension**已经安装并运行

Intune为用户或者设备指派策略后，客户端会自动下载和安装**Intune Management Extension**。

**Intune Management Extension**会自动下载到以下目录：

	%ProgramFiles(x86)%\Microsoft Intune Management Extension

![](/images/119.png)

打开Services.msc, 可以看到**Microsoft Intune Management Extension**已经在运行。

![](/images/120.png)

# 客户端检查策略的时间间隔

**Intune Management Extension**每1小时会向Intune检查PowerShell脚本或者策略的变化。

# 什么时候PowerShell脚本会自动运行

只有当计算机重启，或者重启**Microsoft Intune Management Extension**服务以后，PowerShell脚本才会运行

# 如何查看日志

日志的路径：

	\ProgramData\Microsoft\IntuneManagementExtension\Logs


在该目录下，可以看到两个日志文件：**AgentExecutor.log**和**IntuneManagementExtension.log**。

用CMTrace日志分析工具，打开IntuneManagementExtension.log文件

从日志内容中，可以看到**Intune Management Extension**获取到了1条策略，该策略中的PowerShell脚本被存储在以下路径：Script file **C:\Program Files (x86)\Microsoft Intune Management Extension\Policies\Scripts\da76b36f-9ac7-453f-9406-ba173e26a608_a9cfc067-3e48-4fa0-bf2d-2bad21fa9e0d.ps1 **is generated.

![](/images/121.png)

用CMTrace日志分析工具，打开AgentExecutor.log文件。

日志中的以下内容，说明脚本已经运行成功。

	Powershell script is successfully executed.


![](/images/122.png)