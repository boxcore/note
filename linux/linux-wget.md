Linux wget命令
=============

## 参数详解

```bash

## 常用参数
-t,--timeout=SECONDS ：设置超时时间
-A,--user-agent="UA信息" ：设置自定义UA信息（参考： User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.9; rv:32.0) Gecko/20100101 Firefox/32.0）
-P "DIR_PATH" ：指定下载到哪个目录
-r ：递归下载
    -nd ：递归下载时不创建一层一层的目录，把所有的文件下载到当前目录
-np ：表示不下载旁站连接
-k ：表示将下载的网页里的链接修改为本地链接
-p ：获得所有显示网页所需的元素
-c,--continue ：断点续传
-i ：后面跟一个文件，文件内指明要下载的URL
-q,--quiet ：安静模式(没有输出)
-b,--background ：启动后转入后台执行
--bind-address=ADDRESS ： 指定本地使用地址(主机名或IP，当本地有多个IP或名字时使用)
-w,--wait=SECONDS : 两次尝试之间间隔SECONDS秒
-Y, --proxy=on/off : 打开或关闭代理
```
- 参考：https://cloud.tencent.com/developer/article/1626127

## 应用场景


### 批量下载或递归下载网页中的所有文件

```bash
wget -r http://site.com/content_dir

## 其他镜像用法：
wget -m -L –reject = http://www.***.com/***/
wget -m http://www.***.com/***/ # 一般情况下使用-m参数就可以
```

### 指定下载编码后再重命名

```bash
wget --restrict-file-names=ascii -m www.xxx.com/
```

下载为ascii的文件名, 可以使用软件RenamePro8.0在“高级文件名变”更里面有一个“文件名编码与解码”，“ANSI编码URL字符串转换为文字”



------------

__参考__

- <http://moper.me/wget-download-the-file-name-garbled.html>
- <http://rubyer.me/blog/111/>