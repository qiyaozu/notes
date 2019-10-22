---
title: Mysql for mac 配置
---

主要参考了：https://blog.csdn.net/qq_32180569/article/details/83417656这篇文档
## Mysql8.0版本更新密码的方式有点不一样，看了很多文章都是使用旧版的方法，一直报错1064错

### 终端启停Mysql
```code
启动MySQL服务： sudo /usr/local/MySQL/support-files/mysql.server start

停止MySQL服务： sudo /usr/local/mysql/support-files/mysql.server stop

重启MySQL服务： sudo /usr/local/mysql/support-files/mysql.server restart
```

1. 停止Mysql服务，我发现在系统设置里面停止，有时候会停止不了，建议使用命令行停止
2. 重置密码：
```code
cd /usr/local/mysql/bin/
sudo su
# 下面命令注意一下，如果是更新密码的话，执行：./mysqld_safe
./mysqld_safe --skip-grant-tables &

新建一个终端：
/usr/local/mysql/bin/mysql -u root -p
如果是更新密码，下面需要输入旧密码，如果是第一次设置密码，直接回车
ALTER user 'root'@'localhost' IDENTIFIED BY '12345678'; # 建议使用8位密码
FLUSH PRIVILEGES;
sudo /usr/local/mysql/support-files/mysql.server restart
```
