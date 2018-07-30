---
title: koa相关使用
---

# koa的使用

## koa-router可以作为处理API请求，也可以做为页面的相应

### 处理get请求

1.query传参（?后面跟参数）
->  获取参数方式：ctx.request.query.id (注：query是个对象)

2.parems传参 （/后面的参数）

```js
router.get('/home/:id', (ctx, next) => {
  console.log(ctx.params.id)
})
```

->  获取参数方式：ctx.params.id

### 如果是post请求，就要解析客户端发过来的json数据，使用koa-bodyparser来解析

-> 注意：需要在router之前引进来
