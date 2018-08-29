---
title: nuxt相关
---

# NUXT相关

## 打包成多个页面：

  nuxt generate

## 不同页面设置不同的meta

```js
head() {
  return {
    title: "about",
    meta: [
      {
        hid: "description",
        name: "description",
        content: "test vue-meta about"
      }
    ]
  };
}
```

想要配置公共的meta信息: 在 nuxt.config.js 修改header - meta

## layout使用：

```html
<template>
  <div>
    <div>this is index layout</div>
    <!-- 下面这个不能少 -->
    <nuxt/>
  </div>
</template>
```

## 中间键的使用

* 在middleware目录下新建一个auto.j进入一个新的页面之前，验证是否登录
  
## nuxt使用vuex的时候，如果报错，就重新启动一次，真TMD的坑