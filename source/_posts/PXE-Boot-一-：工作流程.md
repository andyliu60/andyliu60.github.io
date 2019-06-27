---
title: PXE Boot(一)：工作流程
date: 2019-06-27 10:07:45
tags:
- SCCM
categories:
- 企业产品
---

PXE启动包含三个对象：PXE服务器，DHCP服务器和客户机

PXE服务器(10.100.100.116)：Windows Server 2016
DHCP服务器(10.100.100.251)：Windows Server 2016

**1. 客户机发送DHCP广播包，向DHCP服务器请求IP地址。同时，客户端在广播包中也同时指明需要寻找PXE服务器。这个过程称为"Discover"。 **

如果DHCP广播包包含PXE请求，数据包中必须包含以下选项：

- **Option(94): Client Network Device Interface**

	目前只有唯一的值：1，该值代表**Universal Network Device Interface (UNDI)**
		
	**Universal Network Device Interface (UNDI)** is an application programming interface (API) for network interface cards (NIC) used by the Preboot Execution Environment (PXE) protocol.

<!-- more -->
- **Option(93): Client System Architecture**

	该值表示系统的架构类型。通常有以下类型：
		
		Type   Architecture Name 
		
		----   -----------------
		
		0	Intel x86PC
		
		1    NEC/PC98
		
		2    EFI Itanium
		
		3    DEC Alpha
		
		4    Arc x86
		
		5    Intel Lean Client
		
		6    EFI IA32
		
		7    EFI BC
		
		8    EFI Xscale
		
		9    EFI x86-64



- **Option(97): Client Machine Identifier**

	设备的唯一标识符GUID。

![](/images/347.png)
![](/images/348.png)

**2. DHCP服务器响应客户机的请求，并且为客户机分配了一个IP地址。**

![](/images/349.png)
![](/images/350.png)

**3. PXE服务器响应客户机的请求，并告知PXE服务器的IP地址。**

PXE服务器响应的数据包中，会包含**Option 60**。

![](/images/351.png)

**4. 客户机向PXE服务器发送请求，询问Network Boot Program(NBP)路径。**

![](/images/352.png)

**5. PXE服务器响应客户机的请求。** 

可以看到：

Boot file name: smsboot\x64\wdsmgfw.efi

![](/images/353.png) 

**6. 客户机通过TFTP服务器下载wdsmgfw.efi文件。**

![](/images/354.png)


参考资料：


- [Dynamic Host Configuration Protocol (DHCP) Options for the Intel Preboot eXecution Environment (PXE)](https://tools.ietf.org/html/rfc4578#page-2)

- [You want to PXE Boot? Don't use DHCP Options.](https://techcommunity.microsoft.com/t5/Configuration-Manager-Blog/You-want-to-PXE-Boot-Don-t-use-DHCP-Options/ba-p/275562)


