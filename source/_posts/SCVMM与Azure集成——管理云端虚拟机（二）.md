---
title: SCVMM与Azure集成——管理云端虚拟机（二）
date: 2019-02-01 09:07:10
tags:
- SCVMM
categories:
- 企业产品
---
在[SCVMM与Azure集成——管理云端虚拟机（一）](https://www.jianshu.com/p/914790311f98)中，介绍了用基于证书（管理证书）认证和授权的方式来对Azure端的虚拟机进行管理。

在VMM1801中，我们可以采用基于Azure AD的认证和授权对ARM和区域相关的Azure进行管理。

#准备工作

- SCVMM 1801
- 创建Azure AD应用
- 应用ID和Key
- Azure订阅ID
- Azure目录ID
- 为应用添加“订阅”的所有者权限

# 创建Azure AD应用

1. 登录Azure Active Directory门户，在“应用注册”中，点击“新应用注册”
![](/images/30.png)

2. 输入新应用的名称和登录URL
![](/images/31.png)

3. 查看已注册应用的ID
![](/images/32.png)

4. 点击“设置” - “密钥”，生成并记录密钥
![](/images/33.png)

# Azure目录ID

通过登录Azure Active Directory 门户，并查看“属性”，可以看到目录ID。
![](/images/34.png)

# Azure订阅ID

请参考[SCVMM与Azure集成——管理云端虚拟机（一）](https://www.jianshu.com/p/914790311f98)查看Azure订阅ID。

# 为应用添加“订阅”的所有者权限

1. 登录Azure门户
2. 在“所有服务”中，查找“订阅”
3. 选择“访问控制（标识和访问管理）”
![](/images/35.png)
4. 为应用添加订阅所有者权限
![](/images/36.png)

# 将SCVMM和Azure集成

1. 在SCVMM Console中，选择“VMs and Services” - “Azure Subscriptions”。点击“Add Subscription”。
![](/images/37.png)

2. 选择“Management using Azure AD authentication”，并输入相应的信息
![](/images/38.png)

3. 添加成功后，可以看到虚拟机的信息和状态。


