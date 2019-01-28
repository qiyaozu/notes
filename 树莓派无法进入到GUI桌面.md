---
title: linux系统无法启动提示give root password for maintenance
---

## 命令行出现：
```
GIVE root password for maintenance

(or type control-D to continue):
```

1. 输入root的密码，进入root账户

2. 重新挂载/，并给予rw读写的权限
```
mount –o remount,rw /
```
3. 编辑/etc/fstab文件：
```
vi /etc/fstab
```
4. 我这里是看到了两个盘，有一个盘前面有个me的标签，把后面的数字改为0即可，当时没有截图，无法具体指示

