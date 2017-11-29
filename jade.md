---
title: jade 相关
---

### jade输出的html页面默认是压缩过的，想要不压缩
  jade -P index.jade

### 对某个文件进行实时监控
  jade -P -w index.jade

### jade标签嵌套
```jade
p
  | 1.banana
  | 2.apple
  span apple1
  | 3.orange
  strong orange1
```

### jade class id的添加
```jade
p.titile#id

// div比较特殊
#id1.side

p(class="title", id="id1")

```

### 注释 单行注释
```jade
// p.title i'm p tag
// 上面的p标签会被输到页面上的
```
```jade
//- p.title i'm p tag
// 上面代码不会被编译到页面中
```

### 块级注释  在其上层添加注释标签
```jade
//-
  p.title lafjlasdflalsdflasdlfjalsdfjl
```

### 变量的声明
```jade
- var jade = 'jade';
```
### 命令行给jade文件传参
  jade -P -w --obj '{"server": "server"}'
> 如果服务器和文件自带的变量重名，优先使用文档声明的变量
### json文件传参
>json文件

```json
{
  "json": "from json"
}

```

 > 命令行
  jade index.jade -P -w -O jade.json
