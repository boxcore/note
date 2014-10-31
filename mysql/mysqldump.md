mysqldump命令
================

mysqldump语法：


mysqldump按条件查找：
mysqldump按条件查找的参数是 -where/-w，例子如：
> mysqldump -uroot -p123456 dbname table_name -where "id>90" > ~/db.sql

## 指定每行都有insert语句和字段
mysqldump -uroot -p123456 cocksucker_online sea_item_effect --extended-insert=false -c --where=" created<='2014-07-17 00:00:00'" > ~/web/db/test.sql

## 解决导出时时区错误问题
mysqldump -uroot -p123456 cocksucker_online sea_item_effect --skip-tz-utc --where=" created<='2014-07-17 00:00:00'" > ~/web/db/test.sql

## 导入导出遇到中文乱码问题
带上参数`--default-character-set=utf8`就指定默认为utf8的。例如：  
mysqldump   -uroot  -p  --default-character-set=utf8   dbname tablename  >  bak.sql  
mysql -uroot -p --default-character-set=utf8 dbname < bak.sql