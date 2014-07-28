Linux内存管理
=============

## linux下手动清理内存－缓存

```bash
free -m
# 释放内存
/bin/sync 
/bin/echo "1">/proc/sys/vm/drop_caches
free -m
```

使用sync命令以确保文件系统的完整性，sync 命令运行 sync 子例程，将所有未写的系统缓冲区写到磁盘中，包含已修改的 i-node、已延迟的块 I/O 和读写映射文件。

/proc是一个虚拟文件系统，我们可以通过对它的读写操作作为与kernel实体间进行通信的一种手段。也就是说可以通过修改/proc中的文件，来对当前kernel的行为做出调整。也就是说我们可以通过调整/proc/sys/vm/drop_caches来释放内存。










---------------------------

__参考__

<http://os.51cto.com/art/201003/186885.htm>