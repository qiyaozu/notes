---
title: stylus使用
---

###  使用一个函数
``` js
add(a, b)
    a + b
```

### 还可以像ES6一样使用默认参数
``` js
add(a, b = 5)
    a + b
```


### 使用unit函数将单位换算成指定单位
``` js
add (a, b = unit(a, px))
    a + b
```