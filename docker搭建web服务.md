---
title: docker 搭建web服务
---

## 设置容器的端口映射：有四种写法
1. 只设置容器端口
```code 
docker run -p 80 -i -t ubuntu /bin/bash
```

2. 同时制定宿主机端口和容器端口
```code
docker run -p 8080:80 ubuntu /bin/bash
```

3. 指定ip和容器端口
```code
docker run -p 0.0.0.0:80 ubuntu /bin/bash
```

4. 指定ip，宿主端口和容器端口
```code
docker run -p 0.0.0.0:8080:80 ubuntu /bin/bash
```

## 在容器中部署nginx服务，以下步骤：
1. 创建80端口的交互式容器
2. 安装nginx
3. 安装vim
4. 创建静态页面
5. 修改nginx配置文件
6. 运行nginx