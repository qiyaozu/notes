---
title: MAC 相关
---

### Mac清理命令
   sudo periodic daily

### 新版本mac系统允许第三方应用程序运行
  sudo spctl --master-disable

### mac使用搜狗的特殊字体快捷键
  ctrl+shift+e

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

### Mac 升级node到最新稳定版
> 在全局安装node的版本管理工具  ： n
  npm install -g n

> sudo 是必须的，latest是最新版，stable是最新稳定版

  n latest

  n stable
  