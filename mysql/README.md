MySQL note
==============


## MySQL连接字符串
```mysql
select CONCAT('My', 'S', 'QL');
-> 'MySQL'
```


## 获取最后插入的ID: LAST_INSERT_ID()
从名字可以看出，LAST_INSERT_ID即为最后插入的ID值，它有2种使用方法:  
一是不带参数：LAST_INSERT_ID()，这种方法和AUTO_INCREMENT属性一起使用，当往带有‘AUTO_INCREMENT’属性字段的表中新增记录时，LAST_INSERT_ID()即返回该字段的值，大家可试下（我已经验证过）；  
二是带有表达式：如上面介绍的LAST_INSERT_ID(value+1)，它返回的是表达式的值，即‘value+1’；  

> SELECT LAST_INSERT_ID();

## 插入系统时间应

now()：以'yyyy-mm-dd hh:mm:ss'返回当前的日期时间，可以直接存到datetime字段中。  
curdate()：’yyyy-mm-dd’的格式返回今天的日期，可以直接存到date字段中。 

> insert into table (name,makedate) values('测试',now());

使用实例1:
```mysql
/*  第一次使用 */
INSERT INTO `cocksucker`.`article` ( `url`, `author_id`, `author`, `last_editor`, `last_checker`, `source`, `title`, `summary`, `item_cat_id`, `item_id`, `sub_title`, `keywords`, `thumb`, `site_id`, `nav_id`, `publish_time`) VALUES ('http://fushi.7808.cn/zixun/52999.html', '1', 'Superman', '', '超级管理员(1)', 'E', '服饰测试文章1', '服饰测试文章1', '9', '0', '服饰测试文章1服饰测试文章1服饰', '服饰测试文章1meta', '', '18', '156', now() );

update article set url= CONCAT('http://fushi.7808.cn/zixun/', LAST_INSERT_ID(), '.html') where id=LAST_INSERT_ID();

/* 第二次使用 */
INSERT INTO `cocksucker`.`article` ( `url`, `author_id`, `author`, `last_editor`, `last_checker`, `source`, `title`, `summary`, `item_cat_id`, `item_id`, `sub_title`, `keywords`, `thumb`, `site_id`, `nav_id`, `publish_time`) VALUES (CONCAT('http://fushi.7808.cn/zixun/', LAST_INSERT_ID()+1, '.html') , '1', 'Superman', '', '超级管理员(1)', 'E', CONCAT('财富商机服饰文章-', LAST_INSERT_ID()+1), CONCAT('财富商机服饰文章-', LAST_INSERT_ID()+1), '9', '0', '财富商机服饰文章副标题', 'meta信息', '', '18', '160', now() );
```
