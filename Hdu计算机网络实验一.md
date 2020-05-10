#### 实验目的

1. 熟悉使用ping、ipconfig(/winipcfg)、netstat、tracert等命令工具来进行测试；
2. 熟悉使用常用网络命令。

#### 实验设备

windows计算机

#### 实验内容

1. 使用Ping工具测试本机TCP/IP协议的工作情况。
2. 使用IPconfig工具测试本机TCP/IP网络配置。
3. 使用Tracert工具测试本机到某主机所经过的路由数。
4. 使用netstat等命令，并分析其结果。

#### 实验过程及结果

##### 使用Ping工具测试本机TCP/IP协议的工作情况

ping 127.0.0.1  测试本机TCP/IP协议的工作情况

出现如下信息说明本机的TCP/IP协议工作正常

![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589087627167.png)



##### 使用IPconfig工具测试本机TCP/IP网络配置

设置计算机为自动获取ip地址

控制面板->网络和Internet->网络和共享中心

![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589087335146.png)

ipconfig  查看自己正在使用的网络参数信息，包括：接口类型、IP地址、子网掩码、默认网关、MAC地址、DNS服务器IP地址等信息

![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589087999230.png)

##### 使用Tracert工具测试本机到某主机所经过的路由数

tracert www.hdu.edu.cn  跟踪计算机到hdu官网之间所经过的路由

![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589089508381.png)

##### 使用netstat等命令

netstat 查看活动的TCP连接

![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589089842644.png)

netstat –a  显示所有活动的 TCP 连接以及计算机侦听的 TCP 和 UDP

netstat -e  显示以太网统计信息

![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589090177297.png)

netstat -f  显示外部地址的完全限定域名

![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589090361782.png)

netstat -n  以数字形式显示地址和端口号

![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589090548053.png)

netstat -o  显示拥有的与每个连接关联的进程ID

![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589091178906.png)

netstat -p proto  显示proto协议的连接，proto可以是TCP,UDP,TCPv6，UDPv6

如 netstat -p TCP  显示TCP协议的连接

![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589091446624.png)

netstat -q  显示所有连接，侦听端口和绑定的非侦听TCP端口

![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589091700924.png)

netstat -r  显示路由表

![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589091740243.png)

netstat -s  显示每个协议的统计信息

![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589091778927.png)

netstat -t  显示当前连接卸载状态

![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589091955922.png)

netstat -x  显示NetWorkDirect 连接，侦听器和共享终结点

netstat -y  显示所有连接的TCP连接模板

![](https://photos-1256949929.cos.ap-shanghai.myqcloud.com/UTOOLS1589092206919.png)

#### 实验总结

经过此次实验，我学会了如何使用Ping，IPconfig，Tracert，netstat等命令分析目前网络的状态情况。其中Ping是平时网络测试中使用最为频繁的工具，它主要用于测试网络的连通性。Ipconfig命令可以查看所有当前的TCP/IP网络配置项。Tracert可用于网络管理和系统性能分析及优化，通过其可以查看信息从本地计算机到达目标计算机所经过的路由。Netstat命令用于显示活动的 TCP 连接、计算机侦听的端口、以太网统计信息、IP 路由表、IPv4 统计信息以及 IPv6 统计信息
