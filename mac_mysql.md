---
title: mac使用mysql
---

* 使用navicat链接本地，本地的是localhost 密码：123456
    > 安装mysql的时候，如果选择了强类型的密码，就不是6位了，要输入八位或以上
* 建库： 右键localhost   new database

* 执行外部的sql表   execute sqlFile

* 在命令行链接数据库 cd  /usr/local/mysql/bin, 然后执行

```code
mysql -u root -p
```

接下来会输入密码： 123456