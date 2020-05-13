---
title: Hdu计算机网络实验三，交换机级联PC之间的互通
author: Legroft
top: false
cover: false
toc: true
mathjax: false
date: 2020-5-12 20:44:51
tags:
- 计算机网络
img:
coverImg:
summary: Hdu计算机网络实验三，交换机级联PC之间的互通
categories:
- 计算机网络
---

> 实验指导书：https://github.com/Legroft/ComputerNetwork

### 实验目的

1.  使用PT仿真软件组建交换机级联网络，完成交换机各种模式进入。
2.  设置交换机的各项基本参数，如时钟、IP等。
3.  端口管理。
4.  跨交换机VLAN配置。

### 实验设备

装有Packet Tracer的windows计算机

### 实验内容

1. 选定交换机的图标，完成拓扑结构、交换机各种模式的进入、交换机的基本配置

2. 设置交换机的各项基本参数，如时钟、IP等

   要求：

   1、 设置交换机的时钟为当前正确的年月日时分秒

   2、 设置主机名为 server 的主机的 IP 地址为 192.168.1.5

   3、 设置交换机的提示符为Sw1

   4、 保存交换机的配置信息

3. 端口管理

4. 跨交换机VLAN的配置

### 实验拓扑及器材

![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589289156761.png)

### 实验过程及结果

#### 实验任务一

##### 选定交换机的图标，完成拓扑结构

1. 选择2950-24交换机和PC，拖到指定位置

![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589289774657.png)

2. 选择直通线连接Switch0和PC0与PC1，Switch1和PC2与PC3。交叉线连接Switch0和Switch1

   ![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589289983156.png)

##### 完成交换机各种模式的进入

了解交换机命令行：

+ 进入特权模式(en)
+ 进入全局配置模式(conf t)
+ 进入交换机端口视图模式(int f0/1)
+ 返回到上级模式(exit) 
+ 从全局以下模式返回到特权模式(end)
+ 帮助信息(如? 、co?、copy?)
+ 命令简写(如 conf t)
+ 命令自动补全(Tab)
+ 快捷键(ctrl+c中断测试,ctrl+z退回到特权视图)
+ Reload重启。(在特权模式下)
+ 修改交换机名称(hostname X)

过程

1. 双击交换机图标----选择CLI标签

2. 熟悉用户模式

3. 熟悉特权模式： en 或 enable

4. 熟悉全局配置模式：conf t 或configure terminal Switch(config)#

5. 接口配置模式：inter f0/1 或 interface fastethernet 0/1 Swtich(config-if)#

6. 双击计算机图标---desktop----ip configuration ，设置IP和子网掩码，PC0\PC1\PC2\PC3分别为192.168.1.1\2\3\4，子网掩码为255.255.255.0

   ![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589290967869.png)

7. 双击计算机图标---desktop----command prompt ，使用ping 不同计算机的IP,查看结果

   例如在PC1上ping 192.168.1.2

![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589291053992.png)

##### 熟悉交换机的基本配置

1.  设置交换机主机名 switch(config)#hostname 主机名

   用户模式下输入:

   en

   conf t

   hostname 主机名

   ![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589291878974.png)

2. 进入特权模式设置密码

   全局设置模式下输入 enable password 密码

   或 enable secret 密码

   

   ![UTOOLS1589291977315.png](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589291977315.png)

   输入两次exit回到用户模式，再输入en进入特权模式，需要输入密码

   ![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589292244467.png)

3.  给2950设置IP地址192.168.1.100 子网掩码为255.255.255.0

   配置设备管理IP地址 

   输入 ip host 192.168.1.100 255.255.255.0

   ![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589292426049.png)

4. 查看交换机相关配置

   特权模式下输入 show run

   ![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589292731744.png)

   输入 show mac-address-table

   ![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589292792616.png)

   输入 show vlan

   ![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589292835466.png)

5. 保存配置

   特权模式输入

   write

   copy run start

   ![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589292898622.png)

#### 实验任务二

1. 设置交换机的时钟为当前正确的年月日时分秒

   特权模式下 clock set 22:23:30 12 May 2020

   验证 show clock

   ![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589293507708.png)

2. 设置主机名为 server 的主机的 IP 地址为 192.168.1.5 

   全局配置模式下输入 ip host 192.168.1.5 255.255.255.0

   ![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589293976610.png)

   

3.  设置交换机的提示符为Sw1

   ![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589294052408.png)

4. 保存交换机的配置信息

   特权模式下输入 write

   ![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589294094848.png)

验证要求

输入 show running-config

​			show startup-config

两者内容相同，说明操作正确

![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589294369364.png)

#### 实验任务三

1. 设置 0/1-8 号端口数据接收和发送的限制带宽为 100M

   输入 

   interface range fastethernet 0/1-8		//进入1-8端口设置

   speed 100														//设置带宽为 100Mbps

   storm-control broadcast level 50			//风暴控制50%

   exit																		返回上一级模式

   ![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589294892336.png)

2. 打开 0/0/1-8号端口的流控功能，把端口9设置为强制100M、全双工，关闭端口9

   输入

   interface fastethernet 0/9

   speed 100

   duplex full

   shutdown

   exit

   ![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589295407356.png)

   验证 输入 show running-config

   ![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589295505464.png)

#### 实验任务四

1. 建立VLAN100，把端口1-4划归VLAN100

2. 建立VLAN200，把端口5-8划归VLAN200

3. 设置VLAN100的IP地址192.168.1.100 掩码255.255.255.0

4. 设置VLAN200的IP地址192.168.1.200 掩码255.255.255.0

5. 把端口9设置为TRUNK口，允许所有VLAN通过

6. 步骤

   switch(config)#vlan 100

   Switch(Config-vlan)# exit

   Switch(Config)# inter vlan 100

   Switch(config-if)#ip address 192.168.1.100 255.255.255.0

   Switch(config-if)#exit

   Switch(config)#interface range fastethernet 0/1-4

   switch(config-if-range)#switchport access vlan 100 

   Switch(config-if-range)#exit

   switch(config)#vlan 200

   Switch(Config-vlan)# exit

   Switch(Config)# inter vlan 200

   Switch(config-if)#ip address 192.168.1.200 255.255.255.0

   Switch(config-if)#exit

   Switch(config)#interface range fastethernet 0/5-8

   switch(config-if-range)#switchport access vlan 200 

   Switch(config-if-range)#exit

   Switch(config)#interface fastethernet 0/9

   Switch(config-if)#switchport  mode  trunk

   Switch(config-if)#switchport  trunk  allowed  vlan  all

   ![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589296444622.png)

   验证 switch#show running-config

   

   ![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589295917163.png)

结果分析：所有配置都非常顺利，一切正常。

### 实验总结

在这个实验中，我熟悉了交换机的用户模式、特权模式、全局配置模式、接口配置模式等，初步了解了交换机的工作原理、基本配置方法和基本指令的用法
