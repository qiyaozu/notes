---
title: 前后端分离，相对安全的token
---

# [JWT](https://jwt.io/introduction/)的使用

看懂下面这张图就可以了  看了官网了解的比较浅
![***](https://cdn.auth0.com/content/jwt/jwt-diagram.png)

前端在接口的请求头里面添加下面的代码，用后天返回的JWT替换掉token

```  js
Authorization: Bearer <token>
```
