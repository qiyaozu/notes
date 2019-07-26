---
title: 使用natapp内网穿透访问本地vue项目无法访问
---

> 映射到本地8080端口，发现报：Invalid Host header,这是由于新版的webpack-dev-server出于安全考虑，默认检查hostname，如果hostname不是配置内的，将中断访问。

### 解决方法：编辑webpack.base.conf.js
```js
module.exports = {
  ... 
  // 添加如下
  devServer: {
    disableHostCheck: true
  }
}
```
natapp的搭建就用说了，[这个](https://natapp.cn/article/natapp_newbie)是快速搭建的图文教程，非常详细了：
这样就可以访问了，试了一下速度不是很快，但是能查看内网就不错了！
