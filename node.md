---
title: node学习
---

# Mac设置全局路径

  export NODE_PATH=/usr/local/lib/node_modules

## node中全局对象 **__dirname** 和 **__filename**

 1. **__dirname** 只包含当前文件的路径
 2. **__filename** 包含路径和文件名

## npm升级某个包的命令

  npm update -g webpack

## pm2常用命令以及解释[参考](https://www.jianshu.com/p/65ebb4ca70d3)

## pm2 启动程序： 先进入app，然后pm2 start app.js || pm2 start npm -- run XXX

## 指定pm2的普通日志文件和错误日志文件：

  pm2 start app.js -o ./logs/out.log -e ./logs/error.log

## pm2自动启动，程序运行完之后运行：

  pm2 save
  pm2 startup

### 或者在根目录下创建config.json

```json
{
  "script"          : "app.js",          // 启动文件
  "error_file"      : "./logs/err.log",  // 错误日志目录
  "out_file"        : "./logs/out.log",
  "merge_logs"      : true,
  "log_date_format" : "YYYY-MM-DD HH:mm Z"
}
```

### nunjucks给页面里面的js赋值

1.普通的赋值

```js
let title = `{{ title }}`
```

2.传对象或者数组
1):传的时候要JSON.stringify
2):在页面上获取的时候需要先解码：

```js
// 参数a是需要解码的数据
function unescapeHTML(a){
    return a.replace(/&lt;/g, "<").replace(/&gt;/g, ">").replace(/&amp;/g, "&").replace(/&quot;/g, '"').replace(/&apos;/g, "'");
}
```

3):JSON.parse
