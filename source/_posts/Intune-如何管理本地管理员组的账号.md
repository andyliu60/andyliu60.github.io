---
title: 'Intune:如何管理本地管理员组的账号'
date: 2020-11-15 16:33:01
tags:
- Intune
---

通常情况下，计算机的本地管理员账号都会被加入到本地管理员组中，这样，本地管理员就会获得计算机的最高控制权。设想如果有几千台计算机，每次在计算机上将管理员账号加入管理员组，将会花费许多的时间。

如果通过Intune一次性推送策略到所有的计算机，就可以在几分钟内，完成添加管理员的操作。关于如何配置和推送Intune策略，请参考以下步骤：

1. 在Intune管理中心，创建一条Windows10平台的自定义策略。
2. 策略的配置参数如下：

```
Name: GroupMember
Description: GroupMember
OMA-URI: ./Device/Vendor/MSFT/Policy/Config/RestrictedGroups/ConfigureGroupMembership
Data type: String
Value： 

<groupmembership>
    <accessgroup desc = "Administrators">
        <member name = "Administrator"/>
        <member name = "admin"/>
        <member name = "AzureAD\intuneadmin@mshybrid.com"/>
        <member name = "S-1-12-1-2425105774-1271028909-3110942359-1029054307"/>
        <member name = "S-1-12-1-1439795316-1275887166-3987366038-750408428"/>
    </accessgroup>
</groupmembership>
```

**注意：**<accessgroup desc = "Administrators"\> 和 </accessgroup\>之间的内容是Administrators组的用户成员。如果要添加一个组，例如Network Configuration Operators，需要增加<accessgroup desc = "Network Configuration Operators"\> ... </accessgroup desc\>。

**另外，尽量按照本地账号、AzureAD账号、SID的顺序添加member name，否则策略可能会推送失败。**

例如：
```
<groupmembership>
    <accessgroup desc = "Administrators">
        <member name = "Administrator"/>
        <member name = "admin"/>
        <member name = "AzureAD\intuneadmin@mshybrid.com"/>
        <member name = "S-1-12-1-2425105774-1271028909-3110942359-1029054307"/>
        <member name = "S-1-12-1-1439795316-1275887166-3987366038-750408428"/>
    </accessgroup>
    <accessgroup desc = "Network Configuration Operators">
        <member name = "netadmin"/>
    </accessgroup>    
</groupmembership>
```

此外：<member name = "S-1-12-1-2425105774-1271028909-3110942359-1029054307"/\>对应的是Azure AD中的Global administrator角色。
<member name = "S-1-12-1-1439795316-1275887166-3987366038-750408428"/\>对应的是Azure AD中的Device administrator角色。
只要Azure AD中的账号被分配了以上任一一种角色，就会拥有本地计算机的管理员权限。

3. 由于OMA-URI是./Device开头，所以该策略只能被分配给**设备组**，而不是用户组。

4. 在本地计算机上，打开计算机管理工具，打开**Administrators**组，可以看到策略已经推送成功。

![](/images/435.png)

