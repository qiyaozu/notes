---
title: pm2
---

### 为什么要使用pm2
PM2是node进程管理工具，可以利用它来简化很多node应用管理的繁琐任务，如性能监控、自动重启、负载均衡等，而且使用非常简单。

### 常用的一些API：
- --watch：监听应用目录的变化，一旦发生变化，自动重启。
- -i：启用多少个实例，可用于负载均衡。如果-i 0或者-i max，则根据当前机器核数确定实例数目。
- --ignore-watch：排除监听的目录/文件
- -n --name：应用的名称。查看应用信息的时候可以用到。
- -o --output <path>：标准输出日志文件的路径。
- -e --error <path>：错误输出日志文件的路径。


### 常用的一些操作：
- 启动：
    pm2 start app.js --watch -n eleme -e 

- 查看node服务列表：
    pm2 list

- 停止某个服务：
    pm2 stop id/name

- 停止所有服务：
    pm2 stop all # 这个只是停止，并没有从列表中删除

- 停止并移除某个服务：
    pm2 delete id/name

- 重启服务
    pm2 restart app.js

### 设置pm2开机启动：

1. pm2 startup
2. 第一步执行完成之后，会让你执行一段命令  直接复制到命令行，回车执行
3. pm2 save （把需要自动启动的服务先执行起来）

