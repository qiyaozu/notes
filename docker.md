---
title: docker 学习
---

## 创建并运行一个容器：
    docker run ubuntu echo "hello world" # ubuntu内核，容器创建成功后，输出hello world

## docker ps -a -l
- -a 列出所有的容器
- -l 列出最新创建的容器

## 查看容器详细信息：
    docker inspect ubuntu

## 运行容器，并进入到容器，并在命令行进行交互
    docker run -i -t ubuntu

## 如果要运行已经存在的容器，需要使用docker start [-i] IMAGE

## 删除容器
    docker rm 容器ID

## 守护式容器：
- 可以长期运行
- 没有交互式会话
- 适合运行应用程序和服务
以守护形式运行容器：
    docker run --name test -d ubuntu /bin/sh -c "while true; do echo hello world; sleep 1;done" 
## 容器在后台运行，再次进入容器：
    docker attach 容器ID

## 查看容器的状态：
    docker logs -tf --tail 0 test # tail后面跟现实最新的几条数据

## 查看运行中容器的进程：
    docker top 容器ID

## 在运行的容器中启动新的进程：
    docker exec -i -t test /bin/bash

## 停止容器
    docker stop 容器ID # 稍微慢点
    docker kill 容器ID # 更快

## 列出镜像
    docker images

## 查看一个镜像的详细信息
    docker inspect imageID

## 删除镜像
    docker rmi imageID