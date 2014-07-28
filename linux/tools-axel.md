axel 下载工具
============

axel tools是多线程下载工具

## 源码编译安装

```bash
wget http://mirrors.boxcore.org/lnmp/axel-1.0b.tar.gz

tar zxvf axel-1.0b.tar.gz
cd axel-1.0b
./configure
make && make install
cd ../
```

## rpm包安装

32位CentOS执行下面命令：

    wget -c http://pkgs.repoforge.org/axel/axel-2.4-1.el5.rf.i386.rpm
    rpm -ivh axel-2.4-1.el5.rf.i386.rpm


64位CentOS执行下面命令：

    wget -c http://pkgs.repoforge.org/axel/axel-2.4-1.el5.rf.x86_64.rpm
    rpm -ivh axel-2.4-1.el5.rf.x86_64.rpm


Debian/Ubuntu安装Axel：

    apt-get install axel


## Axel命令使用方法

axel 参数 文件下载地址
可选参数：

    -n   指定线程数
    -o   指定另存为目录
    -s   指定每秒的最大比特数
    -q   静默模式

如从Diahosting下载lnmp安装包指定10个线程，存到/tmp/：axel -n 10 -o /tmp/ http://soft.vpser.net/lnmp/lnmp0.7-full.tar.gz

如果下载过程中下载中断可以再执行下载命令即可恢复上次的下载进度。
