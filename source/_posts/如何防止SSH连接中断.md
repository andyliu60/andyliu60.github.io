---
title: 如何防止SSH连接中断
date: 2020-07-05 15:31:13
tags:
- RaspberryPi
categories:
- 智能家居

---

修改配置文件**sshd_config**，设置以下参数：

``` 
ClientAliveInterval 30
ClientAliveCountMax 3
```
ClientAliveInterval参数设置为30s，当SSH服务器在30s后没有收到客户端发送的数据，就会向客户端发送一个请求，要求客户端发送一个Keep Alive的消息。

ClientAliveCountMax参数设置为3，就是当SSH服务器在90s仍然没有接收到客户端发送的Keep Alive消息，就会将SSH连接中断。

默认情况下，ClientAliveInterval的参数为0，即SSH服务器不会向客户端发送请求。