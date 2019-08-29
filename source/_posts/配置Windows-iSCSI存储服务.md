---
title: 配置Windows iSCSI存储服务
date: 2019-08-28 10:27:04
tags:
- SCVMM
categories:
- 企业产品
typora-root-url: ..\images
---

本文主要介绍如何配置Windows iSCSI存储服务。

# 术语介绍

**iSCSI**

iSCSI是一种工业标准协议，利用该技术，可以让计算机通过以太网来访问存储设备。

**iSCSI Initiator**





iSCSI Initiator是iSCSI客户端，通过IP网络，向iSCSI Target发送SCSI指令。

**iSCSI Target**

与存储关联的连接目标，用于接收iSCSI Initiator发送的连接请求，并且记录与iSCSI Initiator关联的虚拟磁盘。

**iSCSI Target Server**

运行iSCSI Target的服务器

**iSCSI Virtual Disk**

也可以称为iSCSI LUN，被iSCSI Initiator挂载到本地，以VHD文件形式存在。<!-- more -->

**iSCSI Connection**

允许多个iSCSI Intiator同时与iSCSI Target连接，但是这些iSCSI Intiator必须是在同一个集群中。

**iQN**

iSCSI Initiator和Target的唯一标识符。Initiator的iQN可以通过命令“iscsicli”查询。

# 安装iSCSI Target

1. 打开Server Manager，选择“Add roles and features”。

2. 选择角色“iSCSI Target Server”，点击下一步。

   ![](/images/377.png)

3. 点击安装。

# 配置iSCSI Target

1. 打开Server Manager, 选择“File and Storage Services”。

2. 选择"iSCSI"

   ![](/images/378.png)

3. 打开创建虚拟磁盘向导，创建虚拟磁盘。

   ![](/images/379.png)

4. 选择E盘，点击下一步。

5. 输入虚拟磁盘名称。

   ![](/images/380.png)

6. 输入虚拟磁盘的大小。

   ![](/images/381.png)

7. 创建新的iSCSI Target。

   ![](/images/382.png)

8. 输入iSCSI Target名称。

   ![](/images/383.png)

9. 添加Initiator，输入服务器的FQDN会自动识别iQN。该设置允许添加的Initiator连接给Target。

   ![](/images/384.png)

   ![](/images/385.png)

10. 后续步骤都使用默认设置。

    ![](/images/386.png)

    ![](/images/387.png)

    ![](/images/388.png)

    ![](/images/389.png)

    

# 配置iSCSI Initiator

通常情况下，iSCSI Initiator运行在另外一台服务器上面。默认情况下，iSCSI Initiator服务处于停止运行状态，因此首先需要启用该服务。

1. 打开Server Manager，选择iSCSI Initiator。

   ![](/images/390.png)

2. 选择Yes，启用iSCSI Initiator服务。

   ![](/images/391.png)

3. 选择Discovery，添加iSCSI Target服务器的DNS名称或者IP地址，在服务器上的所有iSCSI Target会被自动发现。

   ![](/images/392.png)

   ![](/images/393.png)

4. 选择需要连接的iSCSI Target，点击Connect。

   ![](/images/394.png)

   ![](/images/395.png)

5. 成功连接后，状态变为Connected。

   ![](/images/396.png)

# 分区和格式化新磁盘

iSCSI连接成功后，在iSCSI Initiator所在服务器上，会出现一块新的磁盘。

1. 通过打开Server Manager，可以看到该磁盘的信息。

   ![](/images/397.png)

2. 右键点击该磁盘，选择Bring Online.

   ![](/images/398.png)

3. 右键点击该磁盘，选择New Volume...

4. 对磁盘进行初始化和分区。

   ![](/images/399.png)

   ![](/images/400.png)

   ![](/images/401.png)

   ![](/images/402.png)

   ![](/images/403.png)

   ![](/images/404.png)

5. 查快新的磁盘分区。

   ![](/images/405.png)



