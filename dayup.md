---
title: 每天进步
---

### MAC查看隐藏文件的快捷键 cmd+shift+.

### MAC 配置java环境
  open ~/.bash_profile
### 把下面的内容添加进去即可
JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk1.8.0_131.jdk/Contents/Home

CLASSPAHT=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar

PATH=$JAVA_HOME/bin:$PATH:

export JAVA_HOME

export CLASSPATH

export PATH


### Python搭建简易的服务器   前提是已经安装了python
1.在任意位置创建一个文件夹  进入
2.执行命令：python -m SimpleHTTPServer
 后面可以跟上想要的端口   不写的话  默认是8000
3.把自己的文件放到这个文件夹里面   例如：test.html
4.打开浏览器firefox 输入localhost:8000/test.html
5.python3的写法： python3 -m http.server 8080


### Mac清理命令
   sudo periodic daily

### 新版本mac系统允许第三方应用程序运行
  sudo spctl --master-disable

### mac使用搜狗的特殊字体快捷键
  ctrl+shift+e
