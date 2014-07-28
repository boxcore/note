排bug日志
============

基础数据说明: 数据库使用0616日线上数据库


## bug 1: 

> Fatal error: MySQL error 1054Unknown column 'tel_400.feedback_status' in 'where clause' in /home/huangchunze/web/romeo/trunk/_xxoo/core/db.fn.php on line 74 

原因: tel_400.feedback_status 字段不存在, 先添加看看.

先添加字段

## bug2 :

> Fatal error: MySQL error 1146Table 'cocksucker_0616.tel_feedback' doesn't exist in /home/huangchunze/web/romeo/trunk/_xxoo/core/db.fn.php on line 74

