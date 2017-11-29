---
title: ES6相关
---

### 浏览器兼容ES6
找到一个安装了babel的node_module的模块   找到browser.min.js

``` js
<script src="browser.min.js"></script>
<script type="text/babel">
   const Name = '张三';//使用新增的关键字：const声明常量
   alert(Name);
</script>
```
