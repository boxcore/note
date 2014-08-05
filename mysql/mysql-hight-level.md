MySLQ高级语法
============

# 正则替换里内容

```sql
update comment set url=IF(url REGEXP 'test.yahoo.com.cn',REPLACE(url,'www1.sohu.com','www.sina.com'),REPLACE(url,'www2.yahoo.com','www.sina.com')) where 1=1;
update comment set author_url=REPLACE(author_url,'sohu','sina') where author_url REGEXP 'www.sohu.com';
```
