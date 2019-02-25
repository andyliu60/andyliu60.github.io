---
title: 'Intune Enrollment: Windows GPO Enrollment'
date: 2019-02-25 13:31:59
tags:
- Intune
categories:
- 企业产品
---
# 安装AD Connect

1. 下载[Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594)
2. 双击安装文件，开始安装。

![](/images/207.png)

<!-- more -->
3. 点击Continue，并选择Use express settings。

![](/images/208.png)

4. 输入Azure AD全局管理员账号和密码，点击Next。

![](/images/209.png)

5. 输入企业AD的管理员账号和密码，点击Next。

![](/images/210.png)

6. 点击Install。

![](/images/211.png)

7. 点击Exit，完成安装。

![](/images/212.png)


# 配置AD Connect

## 选择需要同步的OU

1. 双击Azure AD Connect桌面快捷方式，点击Configure。

![](/images/213.png)

2. 选择Customize Synchronization options, 点击Next。

![](/images/214.png)

3. 输入Azure AD全局管理员账号和密码，点击Next。

![](/images/215.png)

4. 输入企业目录名称，并点击Next。

![](/images/216.png)

5. 选择需要同步的OU，本例为Hybrid，然后点击Next。

![](/images/217.png)

6. 点击Next。

![](/images/218.png)

7. 点击Configure。

![](/images/219.png)

8. 点击Exit。

![](/images/220.png)

## 配置Hybrid Azure AD Join

1. 双击Azure AD Connect桌面快捷方式，点击Configure。
2. 选择Configure device options。

![](/images/221.png)

3. 点击Next。

![](/images/222.png)

4. 输入Azure AD全局管理员账号和密码，点击Next。

![](/images/223.png)

5. 选择Configure Hybrid Azure AD join，点击Next。

![](/images/224.png)

6. 将Authentication Service选为Azure Active Directory，点击Next。

![](/images/225.png)

7. 选择Windows 10 or later domain-joined devices。

![](/images/226.png)

8. 点击Next。

![](/images/227.png)

9. 点击Configure.

![](/images/228.png)

10. 点击Exit。

![](/images/229.png)

## 查看Hybrid中的计算机和用户已经同步到Azure AD。

1. 查看用户op01和op02已经成功同步到Azure AD，来源显示为Windows Server AD

![](/images/230.png)

2. 查看计算机aws05已经成功同步到Azure AD，Join Type时Hybrid Azure AD joined

![](/images/231.png)

# 配置auto-enrollment组策略

1. 下载[Administrative Templates (.admx) for Windows 10 October 2018 Update (1809)](https://www.microsoft.com/en-us/download/confirmation.aspx?id=57576)，并将安装文件保存到域控制器。

2. 在域控制器上，双击安装。
3. 访问目录**C:\Program Files (x86)\Microsoft Group Policy\Windows 10 October 2018 Update (1809) v2\PolicyDefinitions**，拷贝目录en-US和其它所有.admx文件。由于域控制器是英文操作系统，因此，只拷贝en-US目录，其它目录可以不拷贝。

![](/images/232.png)

4. 访问目录**\\azurelab.ml\SYSVOL\azurelab.ml\Policies\PolicyDefinitions**，如果没有目录PolicyDefinitions，可以手工创建。将拷贝的文件粘贴到该目录下。

5. 打开组策略管理器，创建组策略Intune Enrollment。

**Computer Configuration > Policies > Administrative Templates > Windows Components > MDM > Enable automatic MDM enrollment using default Azure AD credentials.**

![](/images/233.png)
![](/images/234.png)

6. 将该组策略链接到OU Hybrid。

# 用域账号登陆计算机，并自动Enroll到Intune。

1. 用域账号op01登陆计算机aws05
2. 用管理员权限打开Task Scheduler。

![](/images/235.png)

3. 在**Task Scheduler Library**, 打开 **Microsoft > Windows** , 然后点击**EnterpriseMgmt**.可以看到正在执行的auto-enrollment计划任务。

![](/images/236.png)

4. 在Azure AD和Intune门户中，可以看到aws05已经enroll成功。

![](/images/237.png)

![](/images/238.png)
