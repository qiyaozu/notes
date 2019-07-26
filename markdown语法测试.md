---
title: markdown语法测试
---

### 0.0.1. 下面是有序列表

1.西游记
2.红楼梦
3.谁许传
4.三国演绎

### 0.0.2. 下面是无序列表

* 苹果
* 香蕉
* 葡萄

### 0.0.3. 让书写的内容居中

 $$ 我就是想居中 $$


### 0.0.4. 引用一段自己的代码
###  ```三个小撇号加上自己的代码个格式  加上格式就会以相应的格式去渲染
```html
 <!--.js #loader {-->
      <!--display: block;-->
      <!--position: absolute;-->
      <!--left: 100px;-->
      <!--top: 0;-->
    <!--}-->
  <!--</style>-->
  <!--<script-->
    <!--src="https://code.jquery.com/jquery-2.2.4.min.js"-->
    <!--integrity="sha256-BbhdlvQf/xTY9gja0Dq3HiwQF8LaCRTXxZKRutelT44="-->
    <!--crossorigin="anonymous"></script>-->
  <!--<script>-->
    <!--// Wait for window load-->
    <!--$(window).load(function () {-->
      <!--// Animate loader off screen-->
      <!--$("#loader").animate({-->
        <!--top: -200-->
      <!--}, 1500);-->
    <!--});-->
  <!--</script>-->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/3.5.2/animate.min.css">
  <link href="/static/css/mint-ui.min.css" rel="stylesheet">
  <link href="/static/css/all.min.css" rel="stylesheet">
  <div>在markdown里面写html语法是比较慢，因为tab不好使</div>
  ```

```htlm
<link href="/static/css/all.min.css" rel="stylesheet">
```

>这是引用名人的一句话

### 测试一下斜体 两种写法

1.在字的左右两边加*号
2.在字的左右两边加_   （下划线）

*里面是斜体字*
_这里面也是斜体字_

### 下面全是在马克飞象说明文档里面看的

@(示例笔记本)[马克飞象|帮助|Markdown]

>一个-外加一个空格表示缩进

- 1.jflajsdfjal 

- **功能丰富** ：支持高亮代码块、*LaTeX* 公式、流程图，本地图片以及附件上传，甚至截图粘贴，工作学习好帮手；

<!-- TOC -->
### <!-- TOC --> 添加这个会对本MD文档做一个总结，就是把所有标题总结到一起

### 最少三个减号表示一个下划线

------

- [0.0.1. 下面是有序列表](#001-下面是有序列表)
- [0.0.2. 下面是无序列表](#002-下面是无序列表)
- [0.0.3. 让书写的内容居中](#003-让书写的内容居中)
- [0.0.4. 引用一段自己的代码](#004-引用一段自己的代码)
- [```三个小撇号加上自己的代码个格式  加上格式就会以相应的格式去渲染](#三个小撇号加上自己的代码个格式--加上格式就会以相应的格式去渲染)

<!-- /TOC -->
##  下划线前面要有一个空行，才会变粗

---

## 最上面一行是显示标题的
| Col1   |     Col2 |   Col3   |Col3   |
| :-- | ---:| :---: |:--: |
| field1    |   field2 |  field3  |suibianla |
| Col1      |     Col2 |   Col3   |zhegebijaio |
| field1    |   field2 |  field3  |我是**最后**|
