svn 迁移到 git

# 安装命令
yum install git-svn
git svn clone http://jiangli-project.googlecode.com/svn/


建立SVN用户到git用户的映射文件，文件格式如下：

    cat /tmp/userinfo.txt
    usr1=usr1<usr1@163.com>
    usr12=usr12<usr12@163.com>


Create a new repository on the command line:
    touch README.md
    git init
    git add README.md
    git commit -m "first commit"
    git remote add origin git@github.com:boxcore/yzl.git
    git push -u origin master

Push an existing repository from the command line

    git remote add origin git@github.com:boxcore/yzl.git
    git push -u origin master
git@github.com:boxcore/Note.git

err:
fatal: remote origin already exists.

    解决办法如下：

    1、先输入$ git remote rm origin


http://jiangli.easymorse.com/?p=509
http://sfzhang88.blog.51cto.com/4995876/1198867

error:http://blog.csdn.net/dengjianqiang2011/article/details/9260435