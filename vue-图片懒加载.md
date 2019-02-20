---
title: 提升用户体验
---

### 图片加载方面，可以使用渐进式图片，或者使用vue-lazyload
```js
// 在main.js
Vue.use(VueLazyload, {
  preLoad: 1,
  loading: require('./assets/loading1.gif'),
  error: require('./assets/error.png')
})
```