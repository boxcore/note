cmake安装
=========

centos6默认安装的cmake版本是2.6的, 这个版本有bug而且很多新软件都需要cmake2.8以上才能运行

卸载cmake:
yum remove cmake # 卸载cmake


安装  wget http://www.cmake.org/files/v2.8/cmake-2.8.12.2-Linux-i386.tar.gz
 tar xvf cmake-2.8.12.2-Linux-i386.tar.gz

建立连接
ln -s /usr/cmake-2.8.12.2-Linux-i386/bin/* /usr/bin/ 

## again
yum install -y libarchive
rpm -ivh cmake-2.8.8-4.el6.i686.rpm

卸载: rpm -e cmake-2.8.8-4.el6.i686

