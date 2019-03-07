---
title: 'SCEP证书(一)：简介'
date: 2019-03-01 14:30:37
tags:
- Intune
categories:
- 企业产品
---
# 术语

**SCEP**

SCEP是**Simple Certificate Enrollment Protocol**的简称，是一种行业标准协议和技术，主要通过企业内部的CA，为网络设备颁发证书。

**NDES**

NDES是**Network Device Enrollment Service**的简称，是基于SCEP协议的服务，可以为网络设备提交证书请求，并将获取到的证书转发给网络设备。


# 步骤

- 部署和安装企业域
- 部署和安装CA
- 部署和安装NDES服务器
- 部署和安装Microsoft Intune Certificate Connector
- 部署和安装Azure AD Application Proxy

# 遇到的问题

- Azure AD Application Proxy和Intune Connector安装在同一台服务器，导致iPhone无法获取到证书。
- Application Proxy的Pre Authentication应该选择Passthrough。



