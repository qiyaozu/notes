---
title: windows下mysql安装
typora-copy-images-to: ..\..\public\img
---

### windows下mysql安装

#### 下载：
https://dev.mysql.com/downloads/mysql/

#### 安装环境变量



环境变量 -> 系统变量  Path 新建(N)

![image-20200304135514128](D:\yaozu_workspace\blog\blog\public\img\image-20200304135514128.png)

#### my.ini文件编写

my.ini文件所在位置：

![image-20200304135627445](D:\yaozu_workspace\blog\blog\public\img\image-20200304135627445.png)

my.ini文件内容：

```
[client]
port=3306
default-character-set=utf8

[mysqld]
# 设置服务器的访问端口和字符集
port=3306
character_set_server=utf8
# 允许最大连接数
max_connections=200
# 设置为自己MYSQL的安装目录
basedir=D:\yaozu_download\mysql-8.0.19-winx64\mysql-8.0.19-winx64
# 设置为MYSQL的数据目录
datadir=D:\yaozu_download\mysql-8.0.19-winx64\mysql-8.0.19-winx64\data
# 创建新表时将使用的默认存储引擎
default-storage-engine=INNODB

```

#### 初始化MySQL

```
mysqld --initialize --user=mysql --console
```

命令执行完毕之后，最后面会有默认密码，等下会用到



![image-20200304141314193](D:\yaozu_workspace\blog\blog\public\img\image-20200304141314193.png)

```
 mysqld --install
```

![image-20200304141428920](D:\yaozu_workspace\blog\blog\public\img\image-20200304141428920.png)

#### 登录mysql

```
mysql -u root -p
```

接下来会让你输入密码，就把刚刚生成的默认密码复制进去

登录进去后，要设置成你容易记住的密码：

```
set password='123'; 
```

#### Bugs

- Client does not support authentication protocol requested by server；

  ```
  use mysql;
  alter user 'root'@'localhost' identified with mysql_native_password by '********';
  flush privileges;
  ```

