---
title: redis
---

### 为什么要使用redis
> 如果有一些数据短时间内不会发生变化，而它们还要被频繁访问，为了提高用户的访问速度和降低服务器的负载，就把这些数据缓存到读取更快的内存中(或者通过较少的计算量就能获取该数据)

### 安装

#### mac 安装
1. brew install redis
2. 启动： brew services start redis

#### linux安装
1. 到[redis官网](https://redis.io)找到最新版本，并使用wget下载到服务器
2. 解压
3. 进入到目录并执行make
4. 把src目录下的redis-server、redis-cli 和redis.conf拷贝到usr/local/redis目录
5. 验证redis是否安装成功： 进入到usr/local/redis，执行./redis-server
6. 设置redis后台启动: cd usr/local/redis
- vi redis.conf
- 在命令行模式下输入/daemonize 把no变为yes (vim 的查找操作)
- ./redis-server redis.conf  就是后台启动redis
7. 进入到交互模式： ./redis-cli


#### 在linux下的简单使用：
```
# 进入到交互模式
./redis-cli

# 设置一个值
set name burgess

# 获取值
get name

# 删除所有数据库中的key
flushall

# 删除当前数据库中的key
flushdb

# 查看所有的key
keys *

# 查看此 key 是否存在
exists key

# 查看当前库中key的数量
dbsize

# 更改key的名字
rename name username

# 删除指定的key，可以同时删除多个
del name 。。。

# 给指定的key设置过期时间 超过过期时间，自动消失
expire key time

# 返回指定key的过期秒数
ttl key

# 选择指定的数据库
select db-index

```

### 对字符串进行操作
- 拼接： 使用append方法：append key string
- 截取：使用substr方法： substr key start_index end_index
- 如果是整数的话，还能进行++、--操作 eg： incr key、 decr key

### 对列表进行操作
- 