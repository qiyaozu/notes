---
title: babel、autoprefix 使用
---

# 因为最近在新公司里面需要大量的写ES5，所以专门折腾了一下babel

参考了一下别人的[博客](https://www.cnblogs.com/zhenwen/archive/2016/07/17/5679589.html)

本来是想借助webpack来运行babel 查看了一下webpack打包的文件会变得比较大，就只是单纯的把ES6变成ES5

1. 全局安装babel-cli

``` code
yarn add babel-cli -g
```

2. 需要安装两个babel插件babel6以及以上

``` code
yarn add babel-preset-es2015 babel-core
```

## 主要命令如下：监视一个文件的改动，并输出到另一个文件

``` code
babel --watch js/index.js -o index.js
```

### 把整个目录输出到另一个目录

``` code
babel src -d dist
```

### 也可以把整个目录的文件打包到一个js中

``` code
babel src -0 index.js
```