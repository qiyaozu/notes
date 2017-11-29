---
title: css 相关
---

### 使页面的内容变成可编辑状态
  -webkit-user-modify: read-write-plaintext-only;

### 响应式解决方案  需要配合rem来使用
```js
document.getElementsByTagName('html')[0].style.fontSize = document.documentElement.clientWidth/10 + "px";
```
```css
div{
  width:1rem;
  height:1rem;
}
```
### 方案2：写页面用320像素去写，然后动态的改变initial-scale, maximum-scale, minimum-scale,缺点是不能在安卓2.2及以下不能兼容
```html
<meta name="viewport" content="width=320,initial-scale=1,minimum-scale=1,maximum=1">
```

### 前天面试的时候被问到，怎样能让一个容器以固定的宽高比例显示
```html
<div class="wrapper">
  <div class="inner"></div>
</div>
```
```css
.wrapper {
  height: 0;
  padding-bottom: 200px;
  position: relative;
  border: 1px solid #ddd;
}
.inner {
  position: absolute;
  top: 0;
  width: 50%;
  height: 50%;
  border: 1px dashed #f00;
}
```

### css3实现平行四边形
![](http://mmbiz.qpic.cn/mmbiz_jpg/zPh0erYjkib1wEDCbVm1BMPF4Ipy9icYLsOVBTDH4t5NxJgrojGIUXX2r32xR9txBS389HP0MuZshnPhYb1N8voQ/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1)

```css
/*因为外层倾斜了之后，内层也会跟着倾斜，所以内层要往相反的方向倾斜*/
.wrapper {
  border: 1px solid #44a5fc;
  color: #333;
  transform: skew(-20deg);
}
.inner {
  transform: skew(20deg);
}
```

### 文字超出显示三个点

```js
word-break:keep-all;

white-space:nowrap;

text-overflow:ellipsis;
```

### 两个span没有放在同一行，中间会有点间距
> 解决办法: 两个span的父元素上添加font-size: 0

### 1px像素边框
```
@media only screen and (-webkit-min-device-pixel-ratio:2) {
  .border1px:after {
    position: absolute;
    height: 1px;
    right: 0;
    width: 100%;
    content: ' ';
    transform: scaleY(0.5);
    -webkit-transform: scaleY(0.5);
  }
}
```

### 彩色图片变成黑白
```css
.gray {
    -webkit-filter: grayscale(100%);
    -moz-filter: grayscale(100%);
    -ms-filter: grayscale(100%);
    -o-filter: grayscale(100%);

    filter: grayscale(100%);

    filter: gray;
}
```
