---
title: 利用Intune部署和安装Win32软件
date: 2019-02-12 08:50:46
tags:
- Intune
categories:
- 企业产品
---
Intune除了支持微软商店的软件以外，也支持传统的Win32软件部署和安装，如.msi和.exe格式的安装程序。

下面以[Google Chrome](https://cloud.google.com/chrome-enterprise/browser/download/)为例，介绍整个配置和部署过程。

<!-- more -->

# 转换安装程序的格式为.intunewin

1. 下载程序格式转换工具[Microsoft Win32 Content Prep Tool](https://github.com/Microsoft/Intune-Win32-App-Packaging-Tool)，并将其保存到**D:\Download**目录。

2. 在**D:\Download**目录下，创建新目录**Chrome**

3. 将文件**GoogleChromeStandaloneEnterprise64.msi**和**Chrome.jpg**拷贝到**D:\Download\Chrome**目录

4. 用管理员权限打开CMD命令行窗口。
5. 在命令行窗口中，进入D:\Download目录，并输入以下命令：

		IntuneWinAppUtil -c D:\Download\Chrome -s GoogleChromeStandaloneEnterprise64.msi -o D:\Download\Chrome

		注:-c 安装文件所在的目录，安装文件除了包括.exe或者.msi文件以外，还有如License.txt, .ini文件等等。          
		   -s 安装文件，例如setup.exe或setup.msi
           -o 输出.intunewin文件的保存位置

6. 运行命令后的输入结果。

![](/images/133.png)

7. 在D:\Download目录下，可以看到生成的新文件**GoogleChromeStandaloneEnterprise64.intunewin**。

![](/images/134.png)

# 上传.intunewin文件

1. 在Intune门户中，选择**Client apps > Apps**，点击**Add**。
2. 选择App类型为**Windows app(Win32)**
![](/images/135.png)
3. 上传.intunewin文件

![](/images/136.png)
![](/images/137.png)

4. 输入App信息

![](/images/138.png)

5. 输入安装和卸载程序的命令。 

	**如果是.msi的安装程序，安装命令会自动填写。**

	![](/images/139.png)

	**如果是.exe的安装程序，需要手工输入命令**
		
	**安装命令必须添加/slient参数，否则安装会失败**
	
	**卸载程序的命令可以在已安装该软件的电脑上查看**

![](/images/140.png)

6. 选择硬件架构和操作系统等要求。

![](/images/141.png)

7. 程序是否已经安装的检测规则。

	![](/images/142.png)

	![](/images/143.png)

	MSI produce code会自动读取出来，不需要手工输入。

8. 安装完成后的返回代码，使用默认值即可。

![](/images/144.png)

9. 将该App分配给用户组


# 客户端安装软件

1. 打开**Company Portal**应用。

![](/images/145.png)

2. 选择**Google Chrome**。

3. 点击**Install**安装**Google Chrome**。

![](/images/146.png)

4. 系统提示开始安装软件。

![](/images/147.png)

5. 系统提示软件安装成功。

![](/images/148.png)
![](/images/149.png)