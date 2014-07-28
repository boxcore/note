mysqldump命令
================

mysqldump语法：


mysqldump按条件查找：
mysqldump按条件查找的参数是 -where/-w，例子如：
> mysqldump -uroot -p123456 dbname table_name -where "id>90" > ~/db.sql

