---
title: Hdu计算机网络实验四，动态路由协议RIP的配置
author: Legroft
top: false
cover: false
toc: true
mathjax: false
date: 2020-5-13 16:57:09
tags:
- 计算机网络
img:
coverImg:
summary: Hdu计算机网络实验四，动态路由协议RIP的配置
categories:
- 计算机网络
---

> 实验指导书：https://github.com/Legroft/ComputerNetwork

### 实验目的

配置动态路由协议RIP

### 实验设备

装有Packet Tracer的windows计算机

### 实验内容

1.  构建拓扑结构
2.  基本链接关系和配置
3.  交换机的基本配置
4. 测试

### 实验拓扑及器材

![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589354632992.png)

### 实验过程及结果

##### 构建拓扑结构

基本链接关系和配置如下

| **设备** | **端口号** | **端口IP地址** | **下联设备（端口）** | **下联端口地址** |
| -------- | ---------- | -------------- | -------------------- | ---------------- |
| **ISP**  | f0/0       | 192.168.10.1   | pc1                  | 192.168.10.10    |
| **ISP**  | f0/1       | 192.168.100.1  | RA(f0/1)             | 192.168.100.2    |
| **RA**   | s1/0       | 192.168.110.1  | RB(s1/0)             | 192.168.110.2    |
| **RA**   | s1/1       | 192.168.120.1  | RC(s1/1)             | 192.168.120.2    |
| **RA**   | f0/0       | 192.168.20.1   | swA-pc2              | 192.168.20.10    |
| **RB**   | f0/0       | 192.168.30.1   | swB-PC3              | 192.168.30.10    |
| **RC**   | f0/0       | 192.168.40.1   | swC-pc4              | 192.168.40.10    |

要点

1. 其中建立RA,RB,RC时要进行如下操作

![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589355732986.png)

2. 勾选此选项

   ![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589357733974.png)

   3. 为pc设置gateway，值为上联交换机的端口地址

      ![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589357782517.png)

完成构建拓扑结构

![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589357998167.png)

##### 交换机配置

动态路由配置RA：

Router(config)#router rip

Router(config-router)#network 192.168.20.0

Router(config-router)#network 192.168.100.0

Router(config-router)#network 192.168.110.0

Router(config-router)#network 192.168.120.0

Router(config-router)#exit

Router#write 

动态路由配置RC：

Router(config)#router rip

Router(config-router)#network 192.168.40.0

Router(config-router)#network 192.168.120.0

Router(config-router)#end

Router#write

动态路由配置ISP：

Router(config)#router rip

Router(config-router)#network 192.168.10.0

Router(config-router)#network 192.168.100.0

Router(config-router)#end

Router#write

动态路由配置RB：

Router(config)#router rip

Router(config-router)#network 192.168.30.0

Router(config-router)#network 192.168.110.0

Router(config-router)#end

Router#write

##### 验证

测试PC1与PC2通信

![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589358164491.png)

### 实验总结

在这个实验中，我学会了动态路由协议RIP的配置，并巩固了交换机配置的相关命令的使用。

