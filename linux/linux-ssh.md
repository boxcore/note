Linux ssh
===========

## SSH添加登陆后邮件提醒

**安装sendmail

```bash
sudo apt-get install sendmail   #ubuntu安装
sudo yum install sendmail       #rehat安装
```

**设置发邮件内容

```
#!/bin/sh  

sendmail -t >/dev/null 2>&1 <<EOF  
to:receive@exmaple.com  
from:sender@example.com
subject:$USER@`hostname` login from ${SSH_CLIENT%% *} 

$USER@`hostname` login from ${SSH_CLIENT%% *}
EOF
```

上面的内容放到用户文件`~/.bashrc`中,下次登陆就有邮件提醒了!


## ssh设置github使用多个key

```bash
cat >> ~/.ssh/config <<'EOF'
# github
    Host test.github.com
    HostName github.com
    # Port 8000
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/test
EOF

chmod 600 ~/.ssh/config

cd <project dir>
git clone git@test.github.com:yourname/test.git

```
