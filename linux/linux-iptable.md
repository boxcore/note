Linux iptable 防火墙设置
==========================

配置防火墙规则文件: `/etc/sysconfig/iptables`

启动和关闭防火墙: `service iptables restart|start|stop`

在防火墙中，来往的数据流被称为IP压缩（本文下面也称数据流为IP压缩）。防火墙有三条缺省规则链来过滤IP压缩，分别为：

    INPUT：所有以主机为目的地的IP压缩
    OUTPUT：所有以主机为源的IP压缩
    FORWARD：所有经过主机，但是既不是以主机为源，也不是以主机为目的地的压缩

而我们最关注的是INPUT规则，这样可以屏蔽一些黑客行为，或者局域网共享。下面以centOS 6.5的默认规则为例子，讲解下各条规则大概的意思：

    -A INPUT -m state –state ESTABLISHED,RELATED -j ACCEPT

-m 选项: 装入一个模块（state）。state 模块能够查看一个压缩并判断它的状态是  NEW、ESTABLISHED 还是 RELATED。  
NEW 指內进的压缩属于不是由主机主导的新增连接。  
ESTABLISHED 及 RELATED 指內进的压缩隶属于一条现存的连接，或者与现存的连接有关系。  

这条规则的意思是：以本主机为目的地的IP压缩，如果隶属于现有的连接，则接受（accept）

    -A INPUT -p icmp -j ACCEPT

表示接受icmp协议的IP压缩，icmp协议主要是ping，很多同学在局域网能ping通一台机器，但是无法通过web访问，就是因为开启了icmp协议，但是http等协议没有开，后面会讲解如何解决这个问题

    -A INPUT -i lo -j ACCEPT

这条规则表示接受那些来自本机（localhost或者127.0.0.1的IP压缩）

    -A INPUT -m state –state NEW -m tcp  -p tcp –dport 22 -j ACCEPT

表示表示接受不是由本机引导的新增的，基于端口号22的连接（句子有点长，仔细体会哈）。22端口是ssh连接用的，所以如果你想远程操作机器，需要开启端口22

    -A INPUT -j REJECT –reject-with icmp-host-prohibited

表示拒绝来自已经被禁止的主机的icmp的IP压缩

    -A FORWARD -j REJECTED –reject-with icmp-host-prohibited

表示拒绝经过本机且源自那些已经被禁止的主机的icmp的IP压缩

下面再详细说说各个参数的意思：

-A：表示添加一条规则(add)

相应的还有：-P（设置规则的缺省值，比如-P INPUT ACCEPT表示没有以本机为目的地的IP压缩默认是接受的）

-F（清楚所有存在的规则，好添加新的规则）

-j：表示满足规则执行的相应的操作，意为jump，比如 ……-j ACCEPT就表示满足相应的规则就接受

-i：界面的意思（interface），lo是本机的意思（localhost）

注意，编辑完iptables文件之后，使用service iptables restart重启防火墙，可以使用命令：iptables -L查看规则是否生效

或者使用命令行

（1）重启后永久性生效：

    开启：chkconfig iptables on
    关闭：chkconfig iptables off

（2）即时生效，重启后失效：

    开启：service iptables start
    关闭：service iptables stop

比如局域网中搭建了一台centOS作为服务器，并且建立了LAMP或者LNMP环境，想让局域网中的其他人都能通过web访问该机器，那么先得固定机器的IP地址，将BOOTPROTO改成static，然后将IPADDR设置一个固定的IP（比如192.168.1.22），在设置子网掩码NETMASK（比如255.255.255.0），NETWORK和GATAWAY和DNS等也设置好，然后就是信任来自本局域网的访问了，添加下面的规则到iptables中，再重启防火墙即可。具体如何配置网络看这里：CentOS网络配置详解

    -A INPUT -i eth0 -j ACCEPT                                       #eth0是你的网卡号，用ifconfig -a命令查看你自己的网卡号

或者你想信任来自一系列IP的访问，可以用斜线记法规定IP的范围，比如：

    -A INPUT -s 192.168.1.0/24 -j ACCEPT                #即接受来自192.168.1.0-192.168.1.255的ip区段的IP压缩

或者为每一个IP添加一条规则，但是当IP比较多时会很麻烦，比如

    -A INPUT -s 192.168.1.22 -j ACCEPT

打开80端口的规则

    -A INPUT -p tcp –dport 80 -j ACCEPT