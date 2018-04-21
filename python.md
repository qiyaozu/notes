---
title: python 学习
---

### Python搭建简易的服务器   前提是已经安装了python
1.在任意位置创建一个文件夹  进入
2.执行命令：python -m SimpleHTTPServer
 后面可以跟上想要的端口   不写的话  默认是8000
3.把自己的文件放到这个文件夹里面   例如：test.html
4.打开浏览器firefox 输入localhost:8000/test.html
5.python3的写法： python3 -m http.server 8080


### python爬虫步骤
https://www.liaoxuefeng.com/api/ref/001432004374523e495f640612f4b08975398796939ec3c000/topics?page=1



### pip3升级
  pip3 install --upgrade pip

### python项目运行：把所有的依赖写到以txt文件里面   
  pip install -r requirements.txt

### python虚拟环境 作用是为了和全局的环境分隔开 
>> 安装
  pip install virtualenv

>> 创建虚拟环境目录
  virtualenv venv　　#venv为虚拟环境目录名，目录名自定义

>> 激活环境
  source venv/bin/activate

>> 退出虚拟环境
  source deactivate