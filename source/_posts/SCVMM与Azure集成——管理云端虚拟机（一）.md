---
title: SCVMM与Azure集成——管理云端虚拟机（一）
date: 2019-02-01 08:55:53
tags:
- SCVMM
categories:
- 企业产品
---
SCVMM是一套企业级的虚拟基础架构管理系统，而Azure则是一个公有云平台。通过将Azure订阅与SCVMM集成，我们将可以实现在SCVMM Console 中, 统一管理部署在Azure上的虚拟机。

通过将SCVMM与Azure集成，我们只可以管理通过**Azure Classic Portal**部署的虚拟机。对于Azure虚拟机，我们主要可以执行以下操作：

- 启动(Start)
- 关闭(Stop)
- 关机(Shut Down)
- 重启(Restart)
- 用RDP连接(Connect via RDP)

首先，在进行两者的集成之前，我们需要完成以下准备工作：
- Azure订阅ID
- SCVMMN能访问Internet
- Service Administrator - 拥有Service Administrator权限的Azure账号可以获取到Azure subscription ID和管理证书的信息。
- 管理证书（Management certificate）


# 获取Azure订阅ID

1. 登录Azure门户，请确保登录账号至少是Service Administrator
2. 在“所有服务”中，查找“订阅”
3. 在“订阅”页面中，可以查看订阅ID
![](/images/23.png)

# 管理证书

通过将管理证书与Azure关联后，VMM才可以访问Azure的服务管理API。证书必须符合X.509 v3规范。

1. 在安装有VMM Server的服务器上，通过以下PowerShell命令创建一张自签名的证书，证书将保存在本地计算机的个人目录下。
```
$cert = New-SelfSignedCertificate -DnsName yourdomain.cloudapp.net -CertStoreLocation "cert:\LocalMachine\My" -KeyLength 2048 -KeySpec "KeyExchange"
$password = ConvertTo-SecureString -String "your-password" -Force -AsPlainText
Export-PfxCertificate -Cert $cert -FilePath ".\my-cert-file.pfx" -Password $password
```
2. 将导出的PFX证书文件安装到VMM Console所在的计算机上，证书存储位置：当前用户-个人

3. 用以下命令导出格式为.cer的证书文件。
`Export-Certificate -Type CERT -Cert $cert -FilePath .\my-cert-file.cer`
4. 将导出的cer证书文件上传到Azure。在“订阅” - “管理证书”中，上传证书。
![](/images/24.png)
![](/images/25.png)
# SCVMM和Azure集成

1. 在SCVMM Console中，选择“VMs and Services” - “Azure Subscriptions”。点击“Add Subscription”。
![](/images/26.png)

2. 输入“Display name”， “Subscription ID”，并选择相应的管理证书。
![](/images/27.png)

3. 如果添加Azure订阅成功，就可以看到VM的数量，以及最新的状态。
![](/images/28.png)

![](/images/29.png)