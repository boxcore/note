Linux Crontab定时任务
=====================

## 安装crontab
`yum install crontabs`

说明:

    /sbin/service crond start //启动服务
    /sbin/service crond stop //关闭服务
    /sbin/service crond restart //重启服务
    /sbin/service crond reload //重新载入配置


crontab 格式：

基本格式 :

```
分钟   小时   日   月   星期   命令

*        *      *    *     *       *

第1列表示分钟1～59 每分钟用*或者 */1表示
第2列表示小时1～23（0表示0点）
第3列表示日期1～31
第4列 表示月份1～12
第5列标识号星期0～6（0表示星期天）
第6列要运行的命令

记住几个特殊符号的含义: 
“*”代表取值范围内的数字, 
“/”代表”每”, 
“-”代表从某个数字到某个数字, 
“,”分开几个离散的数字 

# Use the hash sign to prefix a comment
# +—————- minute (0 – 59)
# | +————- hour (0 – 23)
# | | +———- day of month (1 – 31)
# | | | +——- month (1 – 12)
# | | | | +—- day of week (0 – 7) (Sunday=0 or 7)
# | | | | |
# * * * * * command to be executed
```

## 添加crontab任务
`crontab -e`然后输入如:


