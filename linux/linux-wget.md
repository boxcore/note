Linux wget命令
=============



## 应用场景


### 批量下载或递归下载网页中的所有文件

    wget -r http://site.com/content_dir


### 指定下载编码后再重命名

    wget --restrict-file-names=ascii -m www.xxx.com/

下载为ascii的文件名, 可以使用软件RenamePro8.0在“高级文件名变”更里面有一个“文件名编码与解码”，“ANSI编码URL字符串转换为文字”



------------

__参考__

- <http://moper.me/wget-download-the-file-name-garbled.html>
- <http://rubyer.me/blog/111/>