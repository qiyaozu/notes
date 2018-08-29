---
title: css 相关
---

# 使页面的内容变成可编辑状态

  -webkit-user-modify: read-write-plaintext-only;

## 响应式解决方案  需要配合rem来使用

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

![实例](http://mmbiz.qpic.cn/mmbiz_jpg/zPh0erYjkib1wEDCbVm1BMPF4Ipy9icYLsOVBTDH4t5NxJgrojGIUXX2r32xR9txBS389HP0MuZshnPhYb1N8voQ/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1)

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

```css
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

### 安卓机上input获得焦点时，输入框会把整个页面往上挤

1.页面外层元素不能有固定定位，据对定位是可以的
2.input的高度不能用百分比，或者vh，用vw和px是可以的

### input获得焦点时，让整个页面往上移动

```html
<input @focus="move('-20%')">
```

```js
move(val) {this.distance(val)}
```

### icon图标在安卓和ios上显示不一样

```css
.className{
  display: flex;
  align-items: center;
}
```

### flex 新认识的属性  平分多余的空间

```css
justify-content: space-evenly;
```

### 粘性底部布局: 在外层容器中添加

```css
min-height: fill-available;
```

要在底部的元素

```css
margin-top: -13.333333vw;
height: 13.333333vw;
```

### 去掉滚动条

```css
::-webkit-scrollbar {
    width: 0px;
    height: 1px;
}
::-webkit-scrollbar-thumb {
    border-radius: 5px;
    -webkit-box-shadow: inset 0 0 5px rgba(0, 0, 0, 0.2);
    background: rgba(0, 0, 0, 0.2);
}
```

### http-equiv属性详解(转)

[http-equiv属性详解(转)] (http://kinglyhum.iteye.com/blog/827807)

### 改变placeholder的默认颜色

```css
<style>
    input::-webkit-input-placeholder{
        color:red;
    }
    input::-moz-placeholder{   /* Mozilla Firefox 19+ */
        color:red;
    }
    input:-moz-placeholder{    /* Mozilla Firefox 4 to 18 */
        color:red;
    }
    input:-ms-input-placeholder{  /* Internet Explorer 10-11 */ 
        color:red;
    }
</style>
```

### 使用css的sticky实现吸顶效果

1. 设置了sticky的元素，在屏幕范围（viewport）时该元素的位置并不受到定位影响（设置是top、left等属性无效），当该元素的位置将要移出偏移范围时，定位又会变成fixed，根据设置的left、top等属性成固定位置的效果。
2. 缺点：兼容性

![兼容性](https://test123-1257243555.cos.ap-chengdu.myqcloud.com/sticky%E5%85%BC%E5%AE%B9.png?sign=q-sign-algorithm%3Dsha1%26q-ak%3DAKIDrbxHckIbGiy3A6QTtCSZfDf09GG4LGvF%26q-sign-time%3D1534843417%3B1534844317%26q-key-time%3D1534843417%3B1534844317%26q-header-list%3D%26q-url-param-list%3D%26q-signature%3Ddcdd1d36c147376c494c8f78847f7e1828d932b9)

### 文字两端对齐

```html
<div class="flex-jus">
  <!-- 中文后面要跟一个空格 后面要有一个空的span -->
  两 端 对 齐<span></span>
</div>
```

```css
.flex-jus {
  text-align: justify;
  width: 300px;
  height: 100px;
  line-height: 100px;
}
.flex-jus span {
  display: inline-block;
  padding-left: 100%;
}
```

