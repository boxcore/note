Sendmail命令使用
================

安装sendmail
------------
```bash
yum -y install sendmail
chkconfig sendmail on
service sendmail restart
```

发送sendmail邮件
----------------

## 使用命令发送

```bash
sendmail -t <<EOF
From: Thunje Hwang <thunje@gmail.com>
To: abanet@126.om
Cc: freemouse.another@gmail.com //抄送
Bcc: freemouse.test.another@gmail.com //暗送
Subject: 这是一个测试邮件
-----------------
hello test !
-----------------
EOF
```

说明, 只写`to`发送ok,如果有cc和bss在qq邮箱中会进入垃圾邮件中.

