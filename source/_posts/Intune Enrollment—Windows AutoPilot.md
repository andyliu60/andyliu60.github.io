---
title: 'Intune Enrollment: Windows AutoPilot'
date: 2019-02-01 09:59:19
tags:
- Intune
categories:
- 企业产品
---
# 获取设备的硬件信息

1. 用管理员权限打开PowerShell, 然后运行以下命令：

		md c:\HWID		# 在C盘根目录下创建名为HWID的文件夹
		Set-Location c:\HWID		# 进入目录C:\HWID
		Set-ExecutionPolicy Unrestricted		# 设置PowerShell运行的权限
		Install-Script -Name Get-WindowsAutopilotInfo		#下载并安装脚本Get-WindowsAutopilotInfo
		Get-WindowsAutopilotInfo.ps1 -OutputFile AutopilotHWID.csv		#获取设备的硬件信息

2. 在Hyper-V主机上，通过Hyper-V Manager关闭VM。或者，通过PowerShell命令关闭VM。

		Stop-VM -VMName WindowsAutopilot

3. 用以下命令，挂载VHD文件

		Mount-VHD -path (Get-VMHardDiskDrive -VMName WindowsAutopilot).Path

4. 打开资源管理器，可以看到一个新的驱动器盘符，例如F:。打开该盘符，可以找到并拷贝文件**AutopilotHWID.csv**

5. 卸载VHD文件，并启动VM

		Dismount-VHD -path (Get-VMHardDiskDrive -VMName WindowsAutopilot).Path
		Start-VM -VMName WindowsAutopilot

注：除了挂载VHD的方式以外，也可以直接在C:\HWID目录中，通过网络共享，将**AutopilotHWID.csv**文件拷贝出来。

<!-- more -->  

# 重置设备

1. 打开Settings应用，并导航到**Update&Security - Recovery**

![](/images/39.png)

2. 选择"Reset this PC"下面的"Get started"

3. 点击"Remove everything"

![](/images/40.png)

4. 点击"Remove files and clean the drive"

![](/images/41.png)

5. 点击"Next"

![](/images/42.png)

6. 点击"Reset"

![](/images/43.png)

7. 开始重置设备

![](/images/44.png)
![](/images/45.png)

# 配置Azure AD Company Branding

通过浏览器，访问Azure AD门户，导航到**Home > MSHybrid - Company branding**，编辑默认的Company Branding。

![](/images/46.png)
![](/images/47.png)

# 配置Intune

## 上传设备的硬件信息

1. 通过浏览器，访问Intune门户，导航到**Home > Microsoft Intune > Device enrollment - Windows enrollment Windows > Autopilot devices**
![](/images/48.png)

2. 点击"Import"，上传**AutopilotHWID.csv**

![](/images/49.png)

3. 上传成功后，点击"Sync"，会出现新设备的序列号，型号等信息。上传通常需要等待5-10分钟。

![](/images/50.png)

4. 选择该新设备，并点击"Assign User"。在执行OOBE过程中，设备会自动填写指定的用户名，用户只需填入密码。

![](/images/51.png)

![](/images/52.png)

5. 在Azure AD的设备列表中，会出现一个设备条目，该条目的Name为新设备的序列号。

![](/images/53.png)

## 创建设备组

1. 在Azure AD门户中，新建一个组AutoPilot-Devices

2. 点击"Add members"，并查找设备序列号，添加设备

![](/images/54.png)
![](/images/55.png)

## 配置设备Profile

1. 在Intune门户中，导航到**Home > Microsoft Intune > Device enrollment - Windows enrollment > Windows Autopilot deployment profiles**

2. 点击"Create profile"

		Deployment mode: User-Driven
		Join to Azure AD as: Azure AD joined

![](/images/56.png)

3. 点击配置"Out-of-box experience (OOBE)"

![](/images/57.png)

4. 点击新建的Profile, 并点击"Assignments"，选择设备组AutoPilot-Devices

![](/images/58.png)


# 完成设备初始配置

1. 选择"United States"

![](/images/59.png)

2. 选择"US"

![](/images/60.png)

3. 选择"Skip"

![](/images/61.png)

4. 输入密码

![](/images/62.png)

5. 等待设备完成配置后，进入系统。

![](/images/63.png)
![](/images/64.png)