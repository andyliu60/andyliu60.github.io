---
title: 如何配置Windows Server RRAS VPN服务器
date: 2020-11-17 19:18:28
tags:
- Windows
---

按照以下步骤，可以在Windows Server 2016上配置PPTP VPN服务器。

# 安装RRAS服务
1. 打开**Server Manager**，选择**Add roles and features**。
![](/images/436.png)

2. 点击**Next**。
![](/images/437.png)

<!-- more -->

3. 点击**Next**。
![](/images/438.png)

4. 点击**Next**。
![](/images/439.png)

5. 选择**Remote Access**，点击**Next**。
![](/images/440.png)

6. 点击**Next**。
![](/images/441.png)

7. 点击**Next**。
![](/images/442.png)

8. 选择**DirectAccess and VPN(RAS)**和**Routing**，点击**Next**。
![](/images/443.png)

9. 点击**Next**。
![](/images/444.png)

10. 点击**Next**。
![](/images/445.png)

11. 点击**Next**。
![](/images/446.png)

12. 点击**Close**。
![](/images/447.png)

# 初始配置

1. 在**Server Manager**中，打开RRAS配置向导。
![](/images/448.png)

2. 选择**Deploy VPN Only**。
![](/images/449.png)

3. 右键选择**WIN2016(local)**，选择**Configure and Enable Routing and Remote Access**。
![](/images/450.png)

4. 打开配置向导，点击**Next**。
![](/images/451.png)

5. 选择**Custom Configuration**，点击**Next**。
![](/images/452.png)

6. 选择**VPN access**, **NAT**, **LAN routing**，点击**Next**。
![](/images/453.png)

7. 点击**Finish**。
![](/images/454.png)

# 配置认证方式

1. 右键选择**WIN2016(local)**，选择**Properties**。
![](/images/455.png)

2. 选择**Security**，选择**Authentication Methods...**。
![](/images/456.png)

3. 选择**MS-CHAP v2**和**CHAP**两种认证方式。
![](/images/457.png)

# 配置IP地址池

如果内网没有DHCP服务器为VPN客户端分配IP地址，可以通过以下方式在RRAS服务器上配置IP地址池：

1. 右键选择**WIN2016(local)**，选择**Properties**。
![](/images/455.png)

2. 选择**Security**，选择**IPv4**。
![](/images/458.png)

3. 选择**Static address pool**, 点击**Add**。
![](/images/459.png)

# 配置用户账号

1. 打开**计算机管理器**
2. 打开用户**属性**
3. 选择**Dial-in**, 在**Network Access Permission**，选择**Allow access**。
![](/images/460.png)

# 客户端连接

1. 打开**Settings** - **Network&Internet**。
![](/images/461.png)

2. 选择**VPN**，点击**Add a VPN connection。
![](/images/462.png)

3. 选择VPN类型为PPTP，并输入VPN服务器的IP地址或者名称，然后保存。
![](/images/463.png)

4. 点击连接VPN。

5. 在CMD中，输入ipconfig命令可以看到已经获取到VPN服务器分配的IP地址。
![](/images/464.png)

6. 在CMD中，用tracert追踪到VPN服务器内网口IP地址(172.16.1.20)，以及Hyper-V主机的IP地址(172.16.1.1)，都会先经过172.16.1.100。该地址为为RRAS服务器虚拟网口(Internal)的IP地址。
![](/images/465.png)

7. 在RRAS服务器上，打开CMD窗口，并输入ipconfig，可以看到**PPP adapter RAS (Dial In) Interface**的IP地址为172.16.1.100。
![](/images/466.png)
