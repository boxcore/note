DirectAdmin面包设置
=====================

## 默认mysql密码

文件位置: /usr/local/directadmin/scripts/setup.txt



## 设置时区

**1. 修改系统时间
```
mv /etc/localtime /etc/localtime.moved
ln -s /usr/share/zoneinfo/Asia/Chongqing /etc/localtime
```

**2. 修改php时间

```bash
/usr/local/bin/php -i | grep 'Loaded Configuration File' #查看php.ini位置
vim /usr/local/lib/php.ini
```

编辑如下内容

`date.timezone = "Asia/Shanghai"`  
执行重载`service directadmin reload`


**3. 修改mysql时间

使用root账号执行: `SET GLOBAL time_zone = '+08:00'`;  
然后执行`select now()`查看当前时间

