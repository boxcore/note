webbench 模拟并发连接测试网站的负载能力
===============================

Webbench能测试处在相同硬件上，不同服务的性能以及不同硬件上同一个服务的运行状况。webbench的标准测试可以向我们展示服务器的两项内容：每秒钟相应请求数和每秒钟传输数据量。webbench不但能具有便准静态页面的测试能力，还能对动态页面（ASP,PHP,JAVA,CGI）进 行测试的能力。还有就是他支持对含有SSL的安全网站例如电子商务网站进行静态或动态的性能测试。
Webbench最多可以模拟3万个并发连接去测试网站的负载能力。个人感觉要比Apache自带的ab压力测试工具好，安装使用也特别方便。

1. 适用系统：Linux
2. 编译安装

## 编译安装webbench

```bash
yum -y install ctags
mkdir -pv /usr/local/man/man1

wget -c http://mirrors.boxcore.org/webbench-1.5.tar.gz
tar -zxf webbench-1.5.tar.gz
cd webbench-1.5
make
make install
```


## webbench使用

 参数说明：-c表示并发数，-t表示时间(秒)

 > /usr/local/bin/webbench -c 500 -t 30 http://127.0.0.1/test.jpg
　　

__结果示例：__

```
Webbench - Simple Web Benchmark 1.5
Copyright (c) Radim Kolar 1997-2004, GPL Open Source Software.

Benchmarking: GET http://127.0.0.1/test.jpg
500 clients, running 30 sec.

Speed=3230 pages/min, 11614212 bytes/sec.
Requests: 1615 susceed, 0 failed.
```

## 错误解决
错误解决

    [root@localhost webbench-1.5]# make install
    install -s webbench /usr/local/bin
    install -m 644 webbench.1 /usr/local/man/man1
    install: cannot create regular file `/usr/local/man/man1': No such file or directory
    make: *** [install] Error 1
    [root@localhost webbench-1.5]# ls /usr/local/man/man1
    ls: /usr/local/man/man1: No such file or directory
    [root@localhost webbench-1.5]# mkdir /usr/local/man/man1
    mkdir: cannot create directory `/usr/local/man/man1': No such file or directory
    [root@localhost webbench-1.5]# mkdir /usr/local/man/
    [root@localhost webbench-1.5]# mkdir /usr/local/man/man1
    [root@localhost webbench-1.5]# make install
    install -s webbench /usr/local/bin
    install -m 644 webbench.1 /usr/local/man/man1
    install -d /usr/local/share/doc/webbench
    install -m 644 debian/copyright /usr/local/share/doc/webbench
    install -m 644 debian/changelog /usr/local/share/doc/webbench

-------------------

__参考__

- <http://www.cnblogs.com/xiaocen/p/3704192.html>
- <http://blog.csdn.net/zzz_781111/article/details/7027472>
- <http://home.tiscali.cz/~cz210552/webbench.html>
- <http://www.ha97.com/4623.html>


