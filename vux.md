---
title: vux 走坑
---

### 用了scroller组件之后，要想撑高宽度，只能用padding，不能用margin

### scroller组件和popup组件同时使用会有冲突，popup的遮罩层会占据整个页面

### 路由传参的方式
```js
// 这种传参不会显示在url中，但是收到的页面刷新以后，数据会丢失
this.$router.push({name: '/index', params: {
  id: 000,
  count: 9
}})
// 这种会在url中经过encode编码后传过去，数据格式会改变，传之前最后JSON.stringify转化
this.$router.push({name: '/index', query: {
  id: 000,
  count: 9
}})
```
