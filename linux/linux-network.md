Linux网络服务
============

## 相关配置文件

网络服务常用命令: 

> `/etc/rc.d/init.d/network restart|start|stop`（脚本服务启动与关闭)
> > 也可以使用 `service network restart`(同上，是命令执行）


- /etc/hosts (本地主机ip地址映射,可以有多个别名）
- /etc/services (端口号与标准服务之间的对应关系）
- /etc/sysconfig/network（设置主机名，网关，域名）
- /etc/resolv.conf (配置dns)
- /etc/sysconfig/network-scripts/ifcfg-eth0 (网卡配置文件)

## 修改主机名

`vi /etc/sysconfig/network`（设置主机名，网关，域名）。

> HOSTANME=BOXCORE(主机名）（需要重启计算机才有效）
> GATEWAY=192.168.1.1（网关）

## 修改网卡

`vi /etc/sysconfig/network-scripts/ifcfg-eth0`

> DEVICE=eth0(哪张网卡）
> ONBOOT=yes
> BOOTPROTO=static(静态ip状态设置）
> BOOTPROTO=dhcp(dhcp获取）
> IPADDR=192.168.1.8(静态ip地址)
> NETMASK=255.255.255.0
> GATEWAY=192.168.1.1（网关）(如果在此设置网关，则上面的无效）
> MACADDR=00:0C:29:96:38:F8（修改mac地址）(永久有效）

然后执行`service network restart`重启即可


## 配置临时网卡设置

IP配置方法及自动获取ip: 

    ifconfig eth0 192.168.0.10 将采用默认子网掩码
    ifconfig eth0 192.168.0.10 netmask 255.255.255.252 (手动定义子网掩码)
    ifconfig eth0 up(激活网卡）


### 关闭网卡

    ifconfig eth0 down(关闭网卡）
    /etc/sysconfig/netowrk-scripts/ifdown eth0(脚本关闭网卡）或者
    ifdown eth0(指向/sbin/ifdown的符号链接）

### 手动设置获取DHCP IP地址

    ifconfig eth0 -dynamic(手动设置获取dhcp ip地址）

### 图形窗口设置IP的命令`netconfig`

    netconfig是文本窗口的形式设置IP的命令,修改好之后用 
    `service network restart`重启网卡.


### 修改MAC地址

    ifconfig eth0 down
    ifconfig eth0 hw ether 00:00:0c:12:34:56
    /etc/rd.d/init.d/network(上面的修改可存储在此脚本中）
    ifconfig eth0 up



## 常用测试命令

    ping -c 4 172.16.1.1
    route (对内核的ip路由表进行操作，主要对己配置的接口的主机或网络设置静态路由，如通过ifconfig程序配)
    route add -net 192.168.1.0 netmask 255.255.255.0 eth0 (添加一条到192.168.1.0网络的路由条目)
    route del -net 192.168.1.0 netmask 255.255.255.0 （删除路由条目）
    route -C 查看缓冲表
    route -n 查看本地路由表
    traceroute 路由跟踪

> 注：netconfig、ifconfig、route三者结合使用,不用重启系统及服务。

## 创建ADSL连接

    rpm -qa |grep rp-pppoe
    rpm -ivh rp-pppoe* (将光盘)
    route del default(删除默认路由)
    adsl-setup (设置连接)
    adsl-start (连接测试)
    adsl-status (查看状态)
