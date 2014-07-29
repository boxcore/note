Linux释放内存
==================

```bash
free -m //查看内存
sync // 把内存数据同步到硬盘
echo 3 > /proc/sys/vm/drop_caches //删除内存缓存
```