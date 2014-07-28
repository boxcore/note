sudo配置
===========

## 添加sudo用户

    chmod u+w /etc/sudoers
    vim /etc/sudoers # 找到 root ALL=(ALL) ALL 在这行下边添加 dituhui ALL=(ALL) ALL  (ps:dituhui代表是你要添加sudo权限的用户名)
    chmod u-w /etc/sudoers
