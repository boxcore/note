Linux修改默认端口
================

`vim /etc/ssh/sshd_config`  
找到#Port 22一段，这里是标识默认使用22端口，修改为如下：
Port 22
Port 50000
然后保存退出

如果添加了iptables规则, 则需要做相应的修改

`vim /etc/sysconfig/iptables`