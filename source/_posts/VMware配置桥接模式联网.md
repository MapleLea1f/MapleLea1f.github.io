---
title: VMware配置桥接模式联网
date: 2024-09-05 19:10:53
tags: [Linux,CentOS7]
---

# VMware配置桥接模式联网

## 参考教程

[VMware三种网络模式详解 - 大数据老司机 - 博客园 (cnblogs.com)](https://www.cnblogs.com/liugp/p/16410259.html#二bridged桥接模式)

[Linux基础篇：VMware centos7虚拟机网络配置——桥接模式_虚拟机centos 桥接模式-CSDN博客](https://blog.csdn.net/qq_39241682/article/details/137185104#:~:text=Linux基础篇：VMware )

- VMware1——hostonly网络适配器
- VMware8——NAT网络适配器
- VMware0——桥接模式



## 桥接模式是什么？

`什么是桥接模式？桥接模式就是将主机网卡与虚拟机虚拟的网卡利用虚拟网桥进行通信。在桥接的作用下，类似于把物理主机虚拟为一个交换机，所有桥接设置的虚拟机连接到这个交换机的一个接口上，物理主机也同样插在这个交换机当中，所以所有桥接下的网卡与网卡都是交换模式的，相互可以访问而不干扰。在桥接模式下，虚拟机ip地址需要与主机在同一个网段，如果需要联网，则网关与DNS需要与主机网卡一致。其网络结构如下图所示：`
![](/img/bridge.png)



### 1.配置桥接模式的具体网卡

<u>VMware Workstation->编辑->虚拟网络编辑器</u>

![](/img/VMware-1.png)






### 2. 修改虚拟机网卡设置

<u>设置->网络适配器</u>

![](/img/VMware-2.png)


### 3.修改网络配置文件

#### 3.1 查看物理主机IP信息

```bash
ipconfig /all #查看主机IP信息
arp -a #选择主机空闲IP
```
![](/img/VMware-3.png)

#### 3.2 VI编辑网卡配置文件

```bash
BOOTPROTO="static" #设置为静态IP地址
ONBOOT="yes" #启动时是否激活网卡
HWADDR=00:0C:29:8D:D0:91 #可不配置，若要配置见VMware-4.png
IPADDR= #主机空闲IP
NETMASK= #主机子网掩码
GATEWAY= #主机网关
DNS1=8.8.8.8
DNS2=114.114.114.114
```

#### 3.3 重启网卡使配置文件生效

```bash
systemctl restart network
```
![](/img/VMware-4.png)
