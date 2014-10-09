ShadowSocks  For Linux GUI Install
==================================

## Install for Ubuntu

run `./nw app.nw` to install shadowsock, but it would show errer like this
"./nw: error while loading shared libraries: libudev.so.0: cannot open shared object file: No such file or directory"

then you can run `locate udev.so` to see the locate of  'libudev.so', and  then execute 
`sudo ln -s /lib/x86_64-linux-gnu/libudev.so.1 /lib/x86_64-linux-gnu/libudev.so.0`

发现系统里面的文件名跟node-webkit加载的名称并不相同，我们创建一个新的软链接到这个库。



-----------------
- <http://my.oschina.net/FengJ/blog/156334>
- 