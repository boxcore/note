SQL编写规范
===========


## 数据定义语法

### 有关DATABASE语法

使用create database语句, 可以创建一个数据库.在这个过程中, 可以指定默认的字符集和默认的字符串比较方法.


> `<create database statement> = create database [if not exists] <database name> [<database option>...];`
>> `<database option> = [default] character set <character set name> | [default] collate <collate name>`

```sql
create database if not exists `book` character set "utf8" collate "utf8_general_ci";
```


### 有关TABLE语法

#### create table相关语法

> `<create table statement> = create [tmporary] table [if not exists] <table specification> <table structure> [<table option>...]`
>> `<table specification> = [<database name>.] <table name>`
>> `<table structure> = <table schema>`
>>> `<table schema> = (<table element>[,<table element>...])`
>>>> ``

