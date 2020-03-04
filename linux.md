---
title: ubuntu系统学到的知识
---

# ubuntu系统学到的知识

#### 查看一个文本 两种方式

    cat gedit

### 用vscode打开一个文本

    code filename

### 添加环境变量的命令

    sudo gedit /etc/profile

### 添加完环境变量之后，立即生效的命令

    source ~/.bashrc

### 显示隐藏的文件快捷键

    ctrl+h

### maven编译项目,先进入到项目里面，然后

    mvn compile

### sts添加一个项目

```txt
  import -> maven -> exiting maven projext -> 选择编译过的maven项目 -> **变成ss
```

### 查看所有进程

    ps -A    ||   ps -A | grep redis

### 杀死一个命令 -9是强制杀死  5689是进程编号

    kill -9 5689

### 把当前的查询结果输入到一个文件里面

    ll > 1.txt

### 创建一个文件的命令

  cd.>1.txt

### 全局查找一个文件

  find / -name fileName

### 查找指定的程序

    ps -aux | grep nginx || ps -ef | grep nginx

### xz文件的解压：

    xz -d 要解压的文件   然后： tar -xvf 刚刚解压出来的tar包

### 更新阿里云源

```code
echo -e "deb [by-hash=force] http://mirrors.aliyun.com/deepin unstable main contrib non-free \ndeb-src http://mirrors.aliyun.com/deepin unstable main contrib non-free" | sudo tee /etc/apt/sources.list
```

### npm包没法安装，多数情况是usr目录没有操作权限

```code
sudo chown -R $USER /usr
```

### 服务器重新安装系统之后，要做的一些事情

**对本地的ssh进行重置**

```code
vi /Users/yaozu/.ssh/known_hosts  // 把ip以及ip后面的部分给删掉
```

**安装node** 毕竟我是前端嘛，node肯定是少不了,最简单、最省事的方式是先安装nvm

```code
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.31.1/install.sh | bash
source ~/.bashrc
nvm install v10.13.0
```

### ssh的连接数过多，就没法进行ssh连接，所以要经常清理没用sshd

```
// 列出所有的sshd
ps aux | grep sshd
// 查看当前正在使用的sshd
who
// 删除多余的sshid
kill id  //（注意： ps 列出的第一个不要删除）
```


### 修改*/usr*的权限之后，sudo命令就会报错： **sudo: error in /etc/sudo.conf, line 0 while loading plugin 'sudoers_policy'**
```code
解决方式： 

    chmod 644 /usr/lib/sudo/sudoers.so

    chown -R root /usr/lib/sudo
```

### sudo: unable to resolve host iZ2zecsdy8flu603bmdg1bZ
```code
vim /etc/hosts
在localhost后面添加  iZ2zecsdy8flu603bmdg1bZ
```


### node安装的时候，**强烈**建议大家不要用编译安装，太慢了,请使用nvm安装，但是使用nvm安装node之后，每次启动都要nvm use，解决方法:

  nvm alias default stable   

### 查看端口被占用情况
- lsof -i:端口号
- netstat -tunlp|grep 端口号

### 删除目录下所有.xml后缀名的文件
- find . -name '*.xml' -delete
- find . -name "*.xml" -exec rm -rf {} \;

### ubuntu安装mysql，参考链接：
https://blog.csdn.net/qq_38737992/article/details/81090373

```code
sudo apt-get update
sudo apt-get install mysql-server

<!-- 初始化配置 -->
sudo mysql_secure_installation

<!-- 检查mysql的运行状态 -->
systemctl status mysql.service


```
登录的时候： mysql -u root -p密码

### Ubuntu安装redis：sudo apt-get install redis-server

### kali安装nodejs
```code
wget -qO- https://deb.nodesource.com/setup_12.x | sudo -E bash -
apt-get update
apt-get install nodejs
apt-get install npm
```


### Unbutu卡在“waiting for headers”
```code

rm -rf /var/lib/apt/lists/*
rm -rf /var/lib/apt/lists/partial/*
```

### linux下npm安装的全局命令无法执行
https://blog.csdn.net/qq_33788609/article/details/90691574
1. 对当前用户有效
```code
vi ~/.bashrc
export PATH=$PATH:/usr/local/node/bin
```
2. 所有账户均有效
```code
sudo vi /etc/profile
export PATH=$PATH:/usr/local/node/bin
```

### The following packages have unmet dependencies
https://blog.csdn.net/qiqzhang/article/details/87862556


https://github-production-release-asset-2e65be.s3.amazonaws.com/48378947/80a21000-fdc5-11e9-9f07-6de93f1b7ddd?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAIWNJYAX4CSVEH53A%2F20191104%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20191104T155456Z&X-Amz-Expires=300&X-Amz-Signature=698116f5582a724906985da257e7990461f776ec5617e4c9a5601d6f22834b9d&X-Amz-SignedHeaders=host&actor_id=23499946&response-content-disposition=attachment%3B%20filename%3Dfrp_0.29.1_linux_arm.tar.gz&response-content-type=application%2Foctet-stream


### ubuntu安装Golang
```code
<!-- 卸载旧版 -->
sudo apt-get remove golang-go
sudo apt-get remove --auto-remove golang-go

<!-- 安装 -->
wget https://studygolang.com/dl/golang/go1.12.5.linux-amd64.tar.gz
tar -zxvf go1.12.5.linux-amd64.tar.gz 
sudo mv go /usr/local/

<!-- 配置 -->
vim ~/.bashrc

export GOROOT=/usr/local/go              # 安装目录。
export GOPATH=$HOME/go     # 工作环境
export GOBIN=$GOPATH/bin           # 可执行文件存放
export PATH=$GOPATH:$GOBIN:$GOROOT/bin:$PATH       # 添加PATH路径

source ~/.bashrc

<!-- 测试是否安装成功 -->
go version
```

### apt-get update时卡在 waiting for headers
```
rm -rf /var/lib/apt/lists/* 
rm -rf /var/lib/apt/lists/partial/* 

```
