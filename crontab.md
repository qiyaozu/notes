---
title: crontab 定时任务的编写
---

## 进入时间表编写模式
    crontab -e

## * * * * * 五颗星分别表示：分、时、日、月、周

## 查看所有表单任务：
    crontab -l

> 注：第一次添加完任务之后，要重新启动crontab的进程，使用下面的命令：
```
systemctl restart crond
```

## 查看crond当前的状态：
    systemctl status crond

## */2 如果在分的这个位置，就表示每两分钟执行一次

> 注：如果同一时间需要执行多个任务，不能将多个任务放在一行，需要分开写
