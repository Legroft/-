---
title: Hdu计算机网络实验二，Packet Tracer简单局域网组建和配置
author: Legroft
top: false
cover: false
toc: true
mathjax: false
date: 2020-5-11 17:14:45
tags:
- 计算机网络
img:
coverImg:
summary: Hdu计算机网络实验二，Packet Tracer简单局域网组件和配置
categories:
- 计算机网络
---

> 实验指导书：https://github.com/Legroft/ComputerNetwork

#### 实验目的

1. 认识Packet Tracer 。
2. 学习使用Packet Tracer进行拓扑的搭建。
3. 学习使用Packet Tracer对设备进行配置，并进行简单的测试。

#### 实验设备

装有Packet Tracer的windows计算机

#### 实验内容

1. 拖放设备和布置线缆
2. 用GUI界面配置设备
3. 用实时模式测试ping、HTTP和DNS
4. 用模拟模式测试ping、HTTP和DNS
5. 用CLI界面配置设备（**选做**）

#### 实验拓扑及器材

![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589183139260.png)

#### 实验过程及结果

##### 拖放设备和线缆（搭建拓扑）

1. 拖放两台1841路由器，并把一台的Display Name和Hostname改为Local，另一台改为ISP（在config->GLOBAL->Settings下设置）

   ![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589183335515.png)

2. 关闭路由器电源，把WIC-2T（串口*2）模块分别添加到两台路由器，然后重新打开电源

   ![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589183528747.png)

3. 在本地局域网拖一台2950-24交换机

   ![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589183654807.png)

4. 在本地局域网拖两台PC，分别命名为1A和1B

   ![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589183752053.png)

5. 在ISP网络拖一台服务器，命名为cisco

   ![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589183866267.png)

6. 用直通线（Straight-through）分别连接1A和1B的FastEthernet口到交换机的f0/1和f0/2口；用直通线连接Local的f0/0到交换机的   f0/24。选择该线依次点击1A和交换机以及1B和交换机进行连接

   ![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589184120493.png)

   ![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589184600563.png)

   

7. 用交叉线（Cross-over）连接ISP的f0/0口到cisco的FastEthernet口

   ![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589184252441.png)

8. 用串行线（Serial）DCE一端连接ISP的s0/0/0，另一端（DTE）连接Local的s0/0/0

   ![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589184670151.png)

##### 用GUI界面配置设备

|       | **本地局域网（192.168.1.0/24）** |               |
| :---: | :------------------------------: | :-----------: |
|  1A   |           FastEthernet           |  192.168.1.1  |
|  1B   |           FastEthernet           |  192.168.1.2  |
| Local |               F0/0               | 192.168.1.254 |
|       |  **ISP网络（192.168.2.0/24）**   |               |
| Cisco |           FastEthernet           | 192.168.2.253 |
|  ISP  |               F0/0               | 192.168.2.254 |
|       | **点到点WAN（192.168.3.0/24）**  |               |
|  ISP  |              S0/0/0              |  192.168.3.1  |
| Local |              S0/0/0              |  192.168.3.2  |

1. 按照上表配置各个设备各端口的IP地址：在Config->INTERFACE找到相应端口，选择Static IP配置模式，配置IP address和子网掩码，**同时应该注意使端口置为“On”** 

   ![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589185172941.png)

2. 配置ISP的Serial0/0/0端口的clock rate为64000（因为它为DCE端）

   ![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589187212911.png)

3. 配置ISP上的静态路由：选择Config->ROUTING->Static，添加：192.168.1.0（网络号）/255.255.255.0（子网掩码）/192.168.3.2（下一跳）

   ![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589185566387.png)

4. 同上，配置Local上的默认路由：Config->ROUTING->Static，添加0.0.0.0/0.0.0.0/192.168.3.1

5. 在Config->GLOBAL->Settings下配置1A和1B的Gateway为192.168.1.254（即Local），DNS Server为192.168.2.253（即cisco）

   ![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589185972551.png)

6. Config->GLOBAL->Settings下配置cisco的Gateway为192.168.2.254（即ISP）

7. 配置cisco上的DNS服务：Config->SERVICES->DNS下，Service置为On，把cisco.com和192.168.2.253添加

   ![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589186401059.png)

8. 配置cisco上的HTTP服务：Config->SERVICES->HTTP下，Service置为On。（注意，HTTP服务和DNS服务不一定要在同一台服务器实现）

   ![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589186470644.png)

   

##### 用实时模式测试ping、HTTP和DNS

1. 在1A打开命令行（Desktop->Command Prompt），输入“ping 192.168.2.253”，看是否能够连通。以下说明可以连通，配置正确

   ![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589187372459.png)

2. 打开1A的浏览器（Desktop->Web Browser），输入cisco.com，如果成功，会返回主页

   ![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589187468551.png)

   

##### 用模拟模式测试ping、HTTP和DNS

1. 在右下角，把Realtime模式切换为Simulation模式，会弹出一个Simulation Panel的对话框

   ![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589187620334.png)

2. 编辑协议过滤器，只查看ICMP事件

   ![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589187726813.png)

3. 在1A上打开命令行，输入“ping 192.168.2.253”，此时在逻辑工作区可以看到1A上多了一个信封

   ![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589187841333.png)

4. 此时Capture/Forward按钮可以逐步观察信封移动的过程，AutoCapture/Play按钮则可以进行自动演示。要观察信封里的信息，可以单击信封，也可以单击右边事件列表的Info栏

   ![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589188095106.png)

5. 编辑协议过滤器，只查看DNS和HTTP事件

6. 打开1A的浏览器，输入cisco.com，和刚才一样观察信封移动的过程和里面内容的变化。注意DNS和HTTP的配合

   ![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589188604942.png)

#### 实验总结

经过此次实验，我学会了完成局域网的组建和GUI模式下的网络配置，通过ping测试验证网络组建和配置正确，通过HTTP访问网页验证DNS设置是否正确，加深了我对网络连接设备的理解。
