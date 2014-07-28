mysql source
============


### 常见问题: 在win下导入sql文件乱码问题

中文cmd中默认的编码格式是gbk,直接导入linux下导出的utf8编码的文件会出现乱码,故需要特别指定下编码的格式.

```dos
# 在cmd下导出
mysqldump -uroot -p --default-character-set=utf8 mo（dbname） > E://xxxx.sql

# 在cmd下导入
mysql -u root -p --default-character-set=utf8 
use dbname 
source /root/newsdata.sql
```

而且需要注意,在linux中要配置默认编码为:`default-character-set=utf8`