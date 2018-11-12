---
title: weex 学习
---

# weex 学习笔记

之前一直羡慕别的前端会react native,既可以做前端，也可以做原生的app，之前也仅仅是使用Hbuild打包成app可以调用一些硬件，但是确实坑很多，最近面试也是看有的公司需要会weex，之前一直觉得weex会很少公司在用，现在看来还是有很多公司开始尝试了，毕竟weex可以跨三端，而且性能比RN更好，缺点呢，就是目前还不够成熟。

## weex不支持vw为单位，只支持px

## weex打包之后的东西放到Android Studio里面颜色不显示，可能是因为你用了span标签，换成text即可

## 不支持border: 1px solid #ddd这样的写法，要分开写border-width: 1px;

## 颜色使用十六进制，不然会有很多警告

## 超出部分显示...，css属性
```css
lines: 1;
```

