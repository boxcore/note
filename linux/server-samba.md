局域网文件共享服务samba 
========================

samba简写smb, 是linux下局域网共享服务.

## 安装samba

```bash
yum -y install samba    # yum安装smb
rpm -qa | grep samba    # 查看smb是否安装
whereis samba           # 查看smb目录目录

chkconfig smb on        # 开机自启smb服务
chkconfig --list smb　   # 确认 Samba 启动标签，确认 2-5 为 on 的状态

/etc/rc.d/init.d/smb start　# 启动 Samba 服务  
service smb restart     # 重启Samba 同上
```

如果iptables防火墙是启用状态，那么需要添加以下防火墙规则:

    vi /etc/sysconfig/iptables
    # 写入: 
    -A INPUT -m state --state NEW -m tcp -p tcp --dport 139 -j ACCEPT
    -A INPUT -m state --state NEW -m tcp -p tcp --dport 445 -j ACCEPT
    -A INPUT -p udp -m udp --dport 137 -j ACCEPT
    -A INPUT -p udp -m udp --dport 138 -j ACCEPT



## samba配置

> vi /etc/samba/smb.conf

    [global]
    workgroup  =  工作组
    server  string  =  描述
    log  file  =    日志位置
    max  log  size  =  日志最大大小           KB
    security  =  user       安全等级
    user    使用samba用户登录。注意：samba用户由系统用户转变过来。要把用户生成为samba用户，此用户必须已经是系统用户
    share   不用密码
    server  使用验证服务器验证
    domain  域控制器验证
      
    ·share   definitions        共享设置
      
    [共享目录名]
    commetn  =  目录描述
    browseable  =  yes      目录是否对没有权限的用户可见
    writeable  =  yes       可写（要与系统目录权限相与）
    valid  users  =  用户名    用户限制（目录是哪个用户所有）
    path  =  /www           指定共享目录位置


## 添加samba用户

    smbpasswd  -a  username     # 添加samba用户, 用户名必须存在系统用户名中
    smbpasswd  -x  username     # 删除samba用户
    pdbedit  -L 查看samba用户

添加用户和目录后,确认目录下用户的权限:

    mkdir  /pub
    mkdir  /soft
    chmod 777 /pub
    chmod 700 /soft
    chown aa  /soft
    service smb  restart


__注意:__

- samba权限和系统权限取最严格权限
- samba用户必须是系统用户
- 启动的服务名是smb

## 我常用的Samba服务配置


```bash


# 如果要用root账号，需要关闭selinux
# SELINUX=enforcing 修改为 SELINUX=disabled
# 并注释SELINUXTYPE=targeted这一行内容。
if [ -s /etc/selinux/config ]; then
    sed -i 's/SELINUX=enforcing/SELINUX=disabled/g' /etc/selinux/config
    sed -i 's/^SELINUXTYPE=targeted/#SELINUXTYPE=targeted/g' /etc/selinux/config
fi

# samba添加root目录
cat >>/etc/samba/smb.conf<<eof
[root]
comment = Root Stuff
path = /root
public = no
writable = yes
eof

smbpasswd -a root
chkconfig smb on
chkconfig iptables off
service smb restart
reboot
```


## 客户端使用

1. windows：
    
文件夹地址栏: `\\192.168.56.220\www`

如果修改了密码或用户后,验证信息错误,可以在dos下删除缓存
    net  use  *  /del           删除缓存

    net use * /del /y 或 net use \\{servename} /del /y
    net use \\{servername} /user:{username} {password}



2. linux客户端：
    smbclient  //192.168.140.253/soft -U aa

