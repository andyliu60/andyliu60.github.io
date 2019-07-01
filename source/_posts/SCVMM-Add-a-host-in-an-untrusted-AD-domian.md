---
title: 'SCVMM: Add a host in an untrusted AD domian'
date: 2019-07-01 15:38:08
tags:
- SCVMM
categories:
- 企业产品
---

SCVMM可以添加与VMM服务器不在相同域的主机。

# 环境

SCVMM服务器操作系统: Windows Server 2016 
SCVMM版本： SCVMM 2019
Hyper-V Host: Windwos Server 2016

SCVMM所在域: mshybrid.com
Hyper-V主机所在域： azurelab.ml

# 准备事项

- 创建Run-As Account， 该账号必须是azurelab.ml域中的账户，并且必须有Hyper-V主机的本地管理员权限
- 在SCVMM服务器上，必须能解析Hyper-V host的FQDN主机名。可以用nslookup验证。
<!-- more -->
# 添加主机

![](/images/354.png)
![](/images/355.png)
![](/images/356.png)
![](/images/357.png)
![](/images/358.png)
![](/images/359.png)

# 遇到问题

添加主机时，遇到以下问题。通过为VMM服务器和Hyper-V主机安装最新的操作系统补丁后，问题解决。

![](/images/360.png)

# 参考资料

- [SCVMM Host Not Responding. Error 2912– WinRM & The request is not supported (0x80070032)](https://blog.apps.id.au/scvmm-host-not-responding-error-2912-winrm-request-not-supported-0x80070032/)