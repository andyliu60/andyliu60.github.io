---
title: 如何将Azure AD的账号或角色的objectid转换成本地计算机的sid
date: 2020-11-25 19:09:11
tags:
- Intune
---

1. 安装**Azure AD** PowerShell模块

    `Install-Module -Name AzureAD`

2. 用管理员账号登录到Azure AD

    `Connect-AzureAD`

3. 通过以下命令，获取到Azure AD中角色，其中**Device Administrators**和**Company Administrators**（也就是**Global Administrators**）会自动被加入到本地管理员组。

    `Get-AzureADDirectoryRole`

    ![](./images/467.png)

4. 可以通过访问以下链接，下载脚本。该脚本可以将AzureAD中的用户、组和角色的ObjectID转换成SID。

    https://github.com/okieselbach/Intune/blob/master/Convert-AzureAdObjectIdToSid.ps1

5. 关于该脚本作者的博客，请点击以下链接。

    https://oliverkieselbach.com/2020/05/13/powershell-helpers-to-convert-azure-ad-object-ids-and-sids/

