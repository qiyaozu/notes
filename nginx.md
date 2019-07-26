---
title: nginx 学习
---

# nginx配置文件里面的详解

每一个server就是一个虚拟主机，我们有一个当作web服务器来使用

```
listen 80;            代表监听80端口
server_name xxx.com;  代表外网访问的域名
location / {};        代表一个过滤器，/匹配所有请求，我们还可以根据自己的情况定义不同的过滤，比如对静态文件js、css、image制定专属过滤
root html;            代表站点根目录
index index.html;     代表默认主页
```

## mac下,使用brew安装nginx：
安装：

```code
brew install nginx
```

启动：

```code 
brew services start nginx || sudo nginx
```

停止：

```code
brew services stop nginx || sudo nginx -s stop
```

修改nginx配置文件：
vi /usr/local/etc/nginx/nginx.conf

检查修改的配置文件是否可用：
sudo nginx -t # 需要加sudo，不然那会报错

## Windows下Nginx的启动、停止等命令 注：需要在命令提示符里面打开，不能用git bash

1.启动
  C:\server\nginx-1.0.2>start nginx或
  C:\server\nginx-1.0.2>nginx.exe
2.停止
  C:\server\nginx-1.0.2>nginx.exe -s stop或
  C:\server\nginx-1.0.2>nginx.exe -s quit
3.重启 修改配置文件之后需要重启
  C:\server\nginx-1.0.2>nginx.exe -s reload
