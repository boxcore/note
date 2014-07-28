Git如何永久删除文件(包括历史记录)
===============

## 步骤一: 从你的资料库中清除文件

```bash
git filter-branch --force --index-filter 'git rm --cached --ignore-unmatch *.gz' --prune-empty --tag-name-filter cat -- --all
git filter-branch --force --index-filter 'git rm --cached --ignore-unmatch *.tgz' --prune-empty --tag-name-filter cat -- --all
git filter-branch --force --index-filter 'git rm --cached --ignore-unmatch *.zip' --prune-empty --tag-name-filter cat -- --all
```

##步骤二: 推送我们修改后的repo

以强制覆盖的方式推送你的repo, 命令如下:

```bash
git push origin master --force
```


## 步骤三: 清理和回收空间

 虽然上面我们已经删除了文件, 但是我们的repo里面仍然保留了这些objects, 等待垃圾回收(GC), 所以我们要用命令彻底清除它, 并收回空间.

命令如下:

```bash
rm -rf .git/refs/original/
git reflog expire --expire=now --all
git gc --prune=now
git gc --aggressive --prune=now
```


设置完成之后, 你可以使用命令`du -s .git`查看仓库地址空间大小是否有明显减少了. 

---------------
__参考:__

- <https://help.github.com/articles/remove-sensitive-data>
- <http://www.cnblogs.com/shines77/p/3460274.html>
