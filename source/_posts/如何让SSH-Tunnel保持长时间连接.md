---
title: 如何让SSH Tunnel保持长时间连接
date: 2020-07-25 13:39:16
tags:
- RaspberryPi
categories:
- 智能家居
---

autossh可以用来监控SSH连接，并且当SSH连接中断后，自动重连。

`autossh -f -M 0 -NR 0.0.0.0:50022:localhost:22 root@remoteserver -p 12345`

-f autossh运行在后台。即使不用-f参数，autossh也会运行在后台，但是，如果用帐号登录，会提示输入密码。
-M 如果设置为0，就会关闭autossh监控SSH隧道通断的状态。并且，autossh文档也建议使用OpenSSH自身的KeepAlive监控功能。即在sshd_config中设置以下参数：

```
ClientAliveInterval 30 
ClientAliveCountMax 3

```

另外，如何才能让系统自动重启后，让autossh自动连接。修改配置文件：/etc/rc.local ，在exit 0上方添加以下内容：

autossh -f -M 0 -NR 0.0.0.0:50022:localhost:22 root@remoteserver -p 12345

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

# Print the IP address
_IP=$(hostname -I) || true
if [ "$_IP" ]; then
  printf "My IP address is %s\n" "$_IP"
fi

autossh -f -M 0 -NR 0.0.0.0:50022:localhost:22 root@remoteserver -p 12345

exit 0
```