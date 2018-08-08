---
title: ubuntu系统学到的知识
---

# 查看一个文本 两种方式

    cat gedit

## 用vscode打开一个文本

    code filename

## 添加环境变量的命令

    sudo gedit /etc/profile

## 添加完环境变量之后，立即生效的命令

    source ~/.bashrc

## 显示隐藏的文件快捷键

    ctrl+h

## maven编译项目,先进入到项目里面，然后

    mvn compile

## sts添加一个项目

```txt
  import -> maven -> exiting maven projext -> 选择编译过的maven项目 -> **变成ss
```

## 查看所有进程

    ps -A    ||   ps -A | grep redis

## 杀死一个命令 -9是强制杀死  5689是进程编号

    kill -9 5689

## 把当前的查询结果输入到一个文件里面

    ll > 1.txt

## 创建一个文件的命令

  cd.>1.txt

## 全局查找一个文件

  find / -name fileName

## 查找指定的程序

    ps -aux | grep nginx || ps -ef | grep nginx