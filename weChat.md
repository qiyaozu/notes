---
title: 微信小程序相关
---

### 设置和获取全局属性
>设置
  this.globalData.info = '';
>获取
  getApp().globalData.info


### 小程序使用高德地图
> 自己的高德key：89a985e4dfffcf84dfdb400439d3cf44

### 腾讯地图key
> TMDBZ-COI3G-ZRHQR-IF5YB-57NFZ-7BBSP
> issual 长按获取当前鼠标点击的位置

### 小程序实现动画
```html
<view animation="{{animationData}}">{{toastTitle}}</view>
```

```js
createGlobalAnimate() {  // 页面初始化的时候就可以去执行，duration可以不用写，在step里面可以加
  var animation = wx.createAnimation({
    duration: 500,
    timingFunction: 'ease',
  });
  this.animation = animation;
}
showAnimate() {
  animation.opacity(1).step();
  this.setData({
    animationData: animation.export()
  });
},
```

#### 页面之间传参
  wx.navigateTo({url:'/pages/xiangqing/xiangqing?id=上一页的参数'})


### 点击事件传参
```html
<view class='block' bindtap='fun' data-type='{{item}}'></view>
```


```js
fun(e) {
  let type = e.currentTarget.dataset.type;
}
```



