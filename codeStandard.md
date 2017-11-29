---
title: 代码标准
---

# Code Standard

[TOC]

## General

### Module Name

The module named should be named as it meaning, easy to understand and match the requirement documentation.

e.g. Auth -- authentication, used for SignIn, SignOut, SignUp etc.

The module name should be confirmed with PM before you make the decision.


## Components

### Thinking in Vue way

[Thinking in React EN](https://facebook.github.io/react/docs/thinking-in-react.html)
[Thinking in React ZH](http://blog.csdn.net/shilu89757/article/details/42418283)
[Thinking in Vue之一：组件扩展的尝试](https://zhuanlan.zhihu.com/p/24844296)
[Thinking in Vue之二：Vue 与 MV*](https://zhuanlan.zhihu.com/p/25490369)

### How we organize components

A single page app is consist of `Page`s. A `Page` is consist of multiple `components`. The code structure looks as follow:


```
- modules/
  - Todo
    - components
      - TodoHeader.vue
      - TodoFooter.vue
      - TodoList.vue
    - pages
      - TodoPage.vue
```

## API

TODO


---

## HTML 代码风格

### 基本设置

* 2 空格缩进
* UTF-8 编码

### 统一符号

* 所有标签和属性名称一律小写。<br/>
  理由：如果不这么做可能导致与 Angular 的不兼容。
* 属性值一律使用双引号。<br/>
  理由：统一是必须的，难道会有人想统一成单引号？

### 可省略部分

* 在没有特殊需求的情况下不省略可选的结束标签。<br/>
  理由：这样更容易看出标签的范围，但是要注意下面这种特殊情况。

```html
<style>
li { display: inline-block; }
</style>
<ul>
  <li>1</li>
  <li>2</li>
</ul>
<ul>
  <li>1
  <li>2
</ul>
```

* 不省略可选的自结束标签末尾斜杠。<br/>
  理由：它会影响到外部标记语言的解析。

```html
<div>
  <img src="eleme.png" alt="饿了么" />
</div>
```

* 建议自结束标签包含属性时在结束的斜杆前面加空格。<br/>
  理由：这是 XHTML 规范？其实我只是觉得这样比较漂亮。

```html
<input type="text" />
<hr/>
```

* 建议无值属性不写等号和值。<br/>
  理由：这个真没必要写，不过 DOM 操作时可能会写。

```html
<input type="checkbox" checked />
<script src="···" async defer></script>
```

* 所有 `<a>` 必须有 `href` 属性，如果用不到可以置为 `href="javascript:"`。<br/>
  理由：`href` 不是可选属性，只是浏览器能解析而已。

### 最佳实践

* 不要使用 `input` （`<input type="button">` 、 `<input type="submit">`）来代替 `button` <br/>
  理由：给这类 `input` 只设置 `height` 属性的话，在 `safari` 和 `chrome` 下并不会出现意料中的样式。另外，`button` 可以内嵌 HTML，实现更灵活的结构，如：带图标的按钮。

### 声明相关

* 使用 `<!DOCTYPE html>` 作为唯一的 DTD。<br/>
  理由：它简洁，并能在所有浏览器触发标准模式。
* 使用 `<meta charset="UTF-8" />` 指定文件编码。<br/>
  理由：只设置 `charset` 即可，不需要 `Content-Type`。
* 所有页面必须有 `<title>`，并尽可能地在不同页面使用不同的标题。<br/>
  理由：传统 SEO 考量，对于单页应用也可以增加用户体验。

### 结构相关

* 尽可能地简化 HTML 结构。<br/>
  理由：太复杂的结构难以维护。
* 严格遵守标签嵌套规则，禁止让标签出现在不正确的地方。<br/>
  理由：规范没有约束，未来版本可能不兼容。

```html
<!-- 禁止 -->
<dl>
  <dt>...</dt>
  <ul>
    <li>...</li>
  </ul>
</dl>

<!-- 允许 -->
<dl>
  <dt>...</dt>
  <dd>
    <ul>
      <li>...</li>
    </ul>
  </dd>
</dl>
```

### DOM 相关

* 建议不使用 Level 0 的事件绑定。<br/>
  理由：Level 0 的事件绑定是非规范的，而且容易发生冲突。

```html
<!-- 不建议 -->
<button id="btn" onclick="onBtnClick()">ELE</button>
<script>
var onBtnClick=function() {
  // ...
};
// 不建议
btn.onclick = onBtnClick;
</script>
```

但是，`addEventListener` / `attachEvent` 需要做兼容处理，推荐使用框架封装。

```js
// jQuery 方案
$("#btn").click(function() {
  // ...
});
```

```html
<!-- Angular 方案 -->
<button id="btn" ng-click="onBtnClick()">ELE</button>
```

* 不在视图中处理复杂逻辑，事件处理代码过长时做成函数。<br/>
  理由：在视图中堆积逻辑会影响代码阅读和维护。

```html
<!-- 不推荐 -->
<button id="btn" ng-click="'此处省略100字'">ELE</button>
```
```html
<!-- 推荐 -->
<button id="btn" ng-click="onBtnClick()">ELE</button>
```
```js
module.controller('foo', ['$scope', function($scope) {
  // ...
  $scope.onBtnClick = function() {
    '此处省略100字';
  };
}]);
```

### 其它建议

* 给图片添加 `alt` 属性。
* 给无文字超连接添加 `title` 属性。
* 给可视听的替换型元素内添加描述。

```html
<audio>这是一段神奇的音效</audio>
<canvas>这是一个神奇的效果</canvas>
<iframe src="http://ele.me">这是 ele.me 的首页</iframe>
```

---

## SASS 代码风格

### 基本设置

* 2 空格缩进
* UTF-8 编码

### zindex使用规范

`zindex.scss` 用来统一项目中的 z-index 值，方便管理 z-index 的层级关系，避免 z-index 的值过大或者层级相互覆盖。

```SASS
$zindexlist:
  searchbox                /* 搜索框 */
  premiumsign              /* 在 rstblock 中显示的品牌馆图标 */
  dropbox                  /* 显示信息的 hover 浮动框 */
  sidebar                  /* 右侧栏 */
  toolbardropbox           /* 右侧栏显示信息的 hover 浮动框 */
  modalshade               /* 浮动弹出框遮罩 */
  modal                    /* 浮动弹出框 */
```

`$zindexlist` 中的数组元素决定 z-index 值，从上到下 z-index 值越大，层级越高。

#####使用方法：

```SASS
@include zindex($ele);
```

* `$ele` 参数值，需要在 `$zindexlist` 中定义数组元素，注意变量的位置；
* 也可以使用 `$zindexlist` 中的已经定义的数组元素，但需要注意以后增删改不会有影响；
* 只支持正数，负数还是按照普通的方式。

---

## CSS 代码风格

### 基本设置

* 2 空格缩进
* UTF-8 编码

### 空白与格式

* 大括号与选择器之间留空，冒号后面留空，注释内外前后留空。<br/>
  理由：据说这样比较漂亮。
```CSS
/* 我是注释 */
div { /* 我是注释 */ }
span {
  color: red; /* 我是注释 */
}
```
* 在只有一条样式时允许和选择器写到同一行，不强制。<br/>
  理由：写三行太占屏幕空间。
* 一个选择器中有多个样式声明时每条写一行。<br/>
  理由：使报错可以精确到具体的规则上，便于排错。
* 多个选择器使用逗号隔开时写在不同的行，大括号不要另起一行。<br/>
  理由：修改时不容易漏掉逗号后面的选择器。
```CSS
div,
span {
  color: red;
  font-size: 12px;
}
```
* 每条样式声明后面都加上那个分号。<br/>
  理由：复制起来方便。
* 所有最外层引号使用双引号。<br/>
  理由：与 HTML 保持一致。
* 用逗号分隔的多个样式值写成多行。<br/>
  理由：便于阅读与编辑。
```CSS
.block {
  box-shadow: 0 0 0 rgba(#000, 0.1),
              1px 1px 0 rgba(#000, 0.2),
              2px 2px 0 rgba(#000, 0.3),
              3px 3px 0 rgba(#000, 0.4),
              4px 4px 0 rgba(#000, 0.5);
}
```

### 功能限定

* 避免使用 ID 选择器。<br/>
  理由：权重太高，不易维护。
* 禁止使用 @import 引入 CSS 文件。
  理由：各种坑不解释。<br/>

### 命名与模块化

* 0 值的单位建议省略，但不强制。<br/>
  理由：大部分 0 值的单位是没用的。
* 16 进制颜色值中的字母统一小写。<br/>
  理由：切换大小写麻烦。
* 类名中的字母一律小写。<br/>
  理由：它不区分大小写，难道有人想统一大写？
* 类名中只使用字母、数字以及“-”。<br/>
  理由：要是没有限制的话我怕一些猴子使用阿拉伯文。
```CSS
.hello {} /* OK */
.module-title {} /* OK */
.panel-level1 {} /* OK */
.导航栏 /* Fuck */
```

---

## CSS 模块化命名规则

### 基本设置

* 2 空格缩进
* UTF-8 编码

### 声明

兼容 IE 8 以上浏览器。

### 基本命名

**类名使用完整英文单词或抽掉空格的英文词组。**

```CSS
/* 推荐 */
.module {}
.helloworld {}

/* 不推荐 */
.konnichiwa {} /* 非英文单词会导致大家无法正常阅读 */
.modl {} /* 每个人的缩写未必一致，会造成不统一 */
.hello-world {} /* 类名请只使用一个没有分隔[-_]的词 */
```

驼峰写法或下划线分割单词的写法都存在一个问题，我们的主观无法判断单词的分割。比如`yellowgreen`这个单词，如果使用分单词的写法可能被写成`yellowGreen`或`yello_green`，造成风格不统一。

当然，抽掉空格也会带来另外的问题，比如`a synchronous request`和`asynchronous request`的意思是完全相反的，这时候抽掉空格就会出问题。不过这种情况是开发者们可以主动避免的，在代码 review 时也可以找出存在歧义的命名。

另外，在能确保准确描述目标元素的情况下，尽可能地让类名更加简短。

```CSS
.form-submit {} /* 推荐 */
.form-submittingbutton {} /* 不推荐 */
```

组件名称尽量使用名词或抽掉空格的名词性词组，这样可以降低冲突的可能性。

**有且仅当有层级关系时使用“-”连接，比如组件内的元素类名采用组件名“-”子类名的形式：**

```HTML
<div class="uploader">
  <input type="text" class="uploader-text" />
  <input type="button" class="uploader-button" />
</div>
```

这时选择器在 CSS 中应该平行地定义，以便降低优先级，便于覆写。

```CSS
.uploader {}
.uploader-text {}
.uploader-button {}
```

不要求类名的层级结构和 HTML 保持一致。

```HTML
<div class="grid">
  <div>
    <div class="grid-caption">
      <div class="grid-caption-text"></div>
      <div class="grid-caption-button"></div>
    </div>
  </div>
  <ul class="grid-row">
    <li class="grid-cell"></li>
  </ul>
</div>
```

允许模块穿插使用。

```HTML
<div class="header">
  <div class="container"> <!-- 穿插一个别的组件 -->
    <div class="header-logo"></div>
    <div class="header-nav"></div>
  </div>
</div>
```

但不建议在高层级中放置低层级元素，这样会破坏逻辑。

```HTML
<div class="module">
  <div class="module-caption">
    <div class="module-caption-content"> <!-- 推荐:低层嵌入高层 -->
      <div class="module-text"></div> <!-- 不建议:高层嵌如低层 -->
    </div>
    <!-- 允许:同级嵌套 -->
    <div class="module-captioncontent">
      <div class="module-text"></div>
    </div>
  </div>
</div>
```

### 保持结构灵活性

我们的设计应该尽可能地让样式可以用于更多标签。

```HTML
<style>
.section {}
.section-head {}
.section-body {}
</style>
<div class="section">
  <div class="section-head"></div>
  <div class="section-body"></div>
</div>
<dl class="section">
  <dt class="section-head"></dt>
  <dd class="section-body"></dd>
</dl>
```

甚至可以任意调整结构。

```HTML
<style>
.article {}
.article-main {}
.article-title {}
</style>
<div class="article">
  <div class="article-main">
    <div class="article-title">
      <!-- ... -->
    </div>
    <!-- ... -->
  </div>
</div>
<div class="article">
  <div class="article-title">
    <!-- ... -->
  </div>
  <div class="article-main">
    <!-- ... -->
  </div>
</div>
```

### 样式修饰

一个组件可能有多种状态多种样式，可以在组件上添加修饰符来选择所需的样式。

在先前的命名规范中“-”被用于表示组件与其后代元素的关系。如果此处再使用“-”，逻辑上可能造成混乱。

考虑到这些修饰符可能和组件名冲突，在词法上推荐使用状态名词或形容词。

```HTML
<div class="popup success">
  blah blah blah
</div>
<div class="popup warning">
  blah blah blah
</div>
<div class="popup error">
  blah blah blah
</div>
```

在选择器中使用多类来声明其样式。

```CSS
.popup.success {}
.popup.warning {}
.popup.error {}
```

这样可以避免嵌套的冲突问题。

---

## JavaScript 代码风格

### 优先参考

优先参考[Airbnb的代码风格](https://github.com/airbnb/javascript)

### 基本设置

* 2 空格缩进
* UTF-8 编码

### 严格模式

建议打开严格模式，但不要依赖严格模式中语言特性的变化（仅当需要支持 IE8、IE9 时）

```js
'use strict';
```

### 引号

使用单引号，这样可以跟 HTML 的双引号更好的一起工作。

### 分号

在语句（Statement）的结尾加分号

```js

// 不建议
var fn = function() {
  // Long code
} // 没有分号

// 建议
var fn = function() {
  // Long code
}; // 这里有分号

```

以防万一，在可能有坑的地方手工加分号

```js

var f1 = function ff1() {
  return function() {
    return 1;
  };
} // 此处漏写分号
(function() { // 此处调用了上面的ff1，WAT
})();
console.log(f2); // 1

var f2 = function ff2() {
  return function() {
    return 1;
  };
} // 此处漏写分号
// IIFE
;(function() { // 注意前面的分号
})();
console.log(f2); // function

```

或者使用 `void function() {}()` 的写法，见下

### 空白与格式

在二元和三元运算符的符号与操作数之间添加空格，在非行末的 `,` `;` `}` 后添加空格，在 `{` 前添加空格。并在每个逻辑块中间添加空白行。
特别的，在 if、while 等关键字后加空格，与函数调用做区分

```js
// 不推荐
var foo='bar',hello=foo+2,test=true;
function hi(){
  // ...
}
if(foo&&hello){
  // ...
}else if(foo){
  // ...
}else if(! test){
  // ...
}

// 推荐
var foo = 'bar';
var hello = foo + 2;
var test = true;

function hi(arg1, arg2) {
  // ...
}

if (foo && hello) {
  // ...
} else if (foo) {
  // ...
} else if (!test) {
  // ...
}
```

### 注释

使用 `//` 作为注释符，可以使用 `/* */` 作为多行注释符。注释符号与注释内容之间留空，注释的位置尽量放在代码之上：

```js
/*不推荐*/
//不推荐
; // 不推荐

/* 推荐 */
// 推荐
;
```

建议在今后需要完善的代码中注释以 `// TODO`。请在 TODO 后标注你要做的事

```js
if (condition) {
  console.log('尚未实现');
  // TODO: condition 成立时需要做额外的工作
}
```

### 不要为大括号另开一行

```js
// 不推荐
if (foo)
{
  // ...
}

// 推荐
if (foo) {
  // ...
}

// 不允许
return
{
  a: 1
};

// 一定要
return {
  a: 1
};
```

只有一行语句时允许不带括号，但需把语句紧跟当前行后

```js
if (foo) doSomething();
for (var i = 0; i < 10; i++) doSomething();
```

语句太长时写成两行，这时请加大括号

```js

// 不推荐
for (var i = 0; i < 10; i++)
  doSomething(aaaa, bbbb);

// 推荐
for (var i = 0; i < 10; i++) {
  doSomething(aaaa, bbbb);
}

// 因为某些人调试时喜欢注释代码，于是就出现了
for (var i = 0; i < 10; i++)
  // doSomething(aaaa, bbbb);

```

写 `else` 时不要另起一行

```js

// 不推荐
if (test) {
  things1();
  things2();
}
else {
  things3();
}

// 推荐
if (test) {
  things1();
  things2();
} else {
  things3();
}

```

### var 语句

#### 使用变量之前必须先定义，不要定义全局变量。

```js

// 变量 undefinedVar 从未定义过
undefinedVar = 1; // 严格模式中报错
console.log(global.undefinedVar); // 1

// 鉴于 js 中 var 的坑，可以在函数头统一定义所有变量（不强制，我也讨厌把变量定义堆一起。。。）
void function () {
  for (var i = 0; i < arr.length; ++i) {
    (function () {
      console.log(i); // undefined

      // 很长的代码，你已经忘记了之前做了什么
      for (var i = 0; i < 10; ++i) {
        // Do some other things
      }
    })();
  }
}();

// 小心 var 与 closure 合用时的坑
var elements = [ div1, div2, div3 ];
for (var i = 0; i < elements.length; ++i) {
  elements[i].addEventListener('event', function() {
    console.log(i); // 3
  });
}
```

#### 如果变量有初始赋值则使用单独的 `var`：

```js
// 不推荐
var hello = 1, world = 2;

// 推荐
var hello = 1;
var world = 2;
var foo, fee, fxx;
```

另外强调，不推荐使用下面这种风格的变量定义方式。

```js
// 不推荐
var hello = arr.pop(),
    world = arr.pop();
```

```js
// 不推荐
var hello = arr.pop()
  , world = arr.pop();
```

原因：

1. 当需要修改变量定义顺序时不容易做整行移动
2. 过不了 eslint 的 indent 验证

#### 变量的命名

使用以小写字母开头的驼峰命名（camelCase）法：

```js
// 不推荐
var foo_bar = 'hello eleme';

// 推荐
var fooBar = 'hello eleme';
```


### 常量大写

```js
// 不推荐
var prefix = 'http://api.ele.me/v1/';
var Prefix = 'http://api.ele.me/v1/'

// 推荐
var PREFIX = 'http://api.ele.me/v1/';
```


### 使用字面量

```js
// 不建议
var obj = new Object();
var array = new Array();

// 推荐
var obj = {};
var array = [];

// 鉴于 Array 构造函数的特殊性，不建议
var arr1 = new Array(4, 5, 6); // [4, 5, 6]

// 以免与下面混淆
var arr2 = new Array(4); // [ undefined * 4 ]
// 等价于（不推荐）
var arr3 = [];
arr3.length = 4;
// 等价于（不推荐）
var arr4 = [,,,,];
console.log('0' in arr2, '0' in arr3, '0' in arr4); // false, false, false

// 不推荐
var str = new String('str');
console.log(str === 'str'); // false

var bool = new Boolean(false);
if (bool) console.log('wat'); // wat

// 当真需要使用字面量包装类时，使用显式强制转换（请先三思）
var strObject = Object('str');
strObject.customProperty = someValue;

```

### 比较

建议使用 `===`/`!==` 而非 `==`/`!=`。

```js

// 不推荐
function foo(a) {
  if (a == 123) {
    // ...
  }
}

// 推荐
function foo(a) {
  a = Number(a);
  if (a === 123) {
    // ...
  }
}

```

`==` 的规则比较复杂，大家可能记不住。

```js
var a = '';

// false
if (a === 0);

// true
if (a == 0);
```

对于可能不存在的全局引用可以先做如此判断：

```js
if (typeof localStorage !== 'undefined') {
  // 此时访问 localStorage 绝对不会出现引用错误
}
```

或者

```js
if ('localStorage' in self) {
  // 此时访问 localStorage 绝对不会出现引用错误
}
```

但注意它们的区别

```js

var a = undefined;

// 判断一个全局变量是否有声明
'a' in self; // true

// 判断一个变量是否为 undefined 并将未声明的引用作为 undefined 处理
typeof a !== 'undefined'; // false

```

### 避免无必要的 `if` 语句、三元运算符

```js

var arr = [1, 2, 3];

// 不推荐
var flag1 = arr.length > 0 ? true : false;

// 不推荐
var flag2;
if (arr.length > 0) {
  flag2 = true;
} else {
  flag2 = false;
}

// 推荐
var flag3 = arr.length > 0;

```

### 合理的格式化三元运算符

```js

// 不推荐
var flag1 = veryLooooooooooonnnnggggggCondition ? resultWhenTruth : resultWhenFalsy;

// 推荐
var flag2 = veryLooooooooooonnnnggggggCondition
              ? resultWhenTruth
              : resultWhenFalsy;

```

### 复杂逻辑中建议使用显式转换

```js

+num === Number(num);
!!bool === Boolean(bool);
str + '' === String(str);

// 特别的
if (bool)
// 等价于
if (Boolean(bool))
// 故
if ([]) console.log('true'); // true
// 而
if ([] === true) console.log('true'); // 无输出

// 另外
if (Boolean(String(false))) console.log('true'); // true
// 这点在保存 localStorage 时需要注意

```

不要使用 parseInt 做整数转换，如需使用 parseInt，请给它传入第二个参数 10，避免老式浏览器的坑（IE8？）

```js
var floatValue = 123.456;

// 不要
var intValue = parseInt(floatValue);

// 可以用
var intValue2 = floatValue | 0;

// 更显然的
var intValue3 = Math.floor(floatValue);

```

特别地，使用 parseFloat 做部分转换

```js

// 例如有：
// <div id="div" style="width: 10px"></div>

var divWidth = getComputedStyle(document.getElementById('div')).width; // '10px'

console.log(parseFloat(divWidth)); // 10
console.log(Number(divWidth)); // NaN
console.log(+divWidth); // NaN

```

### 函数定义

建议使用表达式来定义函数，而不是函数语句。

```js
// 不推荐
function fee() {
  // ...
}

// 推荐
var foo = function() {
  // ...
};
```

因为函数语句是在进入作用域时声明，破坏了程序从上到下的执行顺序。可能出现定义在 `return` 后的情况。

```js
void function() {
  // 此处可以正常使用函数，但逻辑不清晰
  foo();

  return null;

  function foo() {};
}();

```

只引用一次的函数建议匿名定义，因为名称存在主观因素。

```js
// 不推荐
var foo = function() {
  // ...
};
element.onclick = foo;

// 推荐
element.onclick = function() {
  // ...
};
```

### 自执行函数

```js
// 不推荐
(function() {
  // ...
})();

+function() {
  // ...
}();

// 推荐
~function() {
  // ...
}();

// 推荐
void function() {
  // ...
}();
```

括号和加号不是上下文无关的，可能受到上文缺分号的影响而出现奇怪的问题，这些问题甚至不会报错，极难调试，所以不推荐此种用法，比如：

```js
var a = 1 // 此处无分号

+function() {
  return 2
}();

// 此处 a 的值为 3
```

### 避免嵌套过深

可以使用 `Promise` 解决深层嵌套问题：

```js
// 不推荐
async1(function() {
  // TODO 1
  async2(function() {
    // TODO 2
    async3(function() {
      // TODO 3
    });
  });
});

// 推荐
Promise.resolve()
  .then(function() {
    return new Promise(function(resolve) {
      async1(resolve);
    });
  })
  .then(function() {
    // TODO 1
    return new Promise(function(resolve) {
      async2(resolve);
    });
  })
  .then(function() {
    // TODO 2
    return new Promise(function(resolve) {
      async3(resolve);
    });
  })
  .then(function() {
    // TODO 3
  });
```

### 禁止事项

* 禁止使用未定义的变量
* 禁止使用 `eval`，非用不可时可以使用 `Function` 构造器替代。
* 禁止使用 `with` 语句。
* 禁止在块作用域中使用函数声明语句。

```js
if (true) {
  // 禁止
  function func1() {
    // ...
  }
  // 允许
  var func2 = function() {
    // ...
  };
}
```

* 禁止使用 8 进制词法

```js
// true
if (010 === 8);
```

* 禁止使用 `arguments` 映射

```js
void function(a) {
  arguments[0]++;
  // 此处 a 为 2
}(1);
```

* 禁止使用重名参数
* 禁止使用保留字做变量名如 `interface` 等

---

## 文案风格指南

这是文书表述上的一些文字格式规范，目的在于增强文字的可读性和保持对外形象的一致性，适用范围包括但不限于软件界面、帮助文档等严肃内容平台，博客和微博等网络宣传媒体平台的用词风格可较轻松活泼些。本指南会不断增补修订。

### 标点符号
中文文书原则上请使用全角标点符号，英文文书请使用半角标点符号。中英夹杂原则上请使用全角标点符号。下面有另行规定者例外。

- 括号的使用：中文文书中，括号中包括数字时采用半角括号，并在括号外留一个空格（连续两个标点符号之间不留空格）。例如：「全部联系人 (12)」。
- 英文文书逗号和句号后请留一个半角空格；中英夹杂文书中英文 (包括数字) 与汉字之间留一个半角空格。
	- 正确：「这是 1 只 HTC 手机」错误：「这是1只HTC手机」
	- 正确：「2011 年 8 月 14 日」错误：「2011年8月14日」
- 百分号写法：56.8% 是对的，56.8 % 是错的。百分号和它前面的数字之间不留空格。
- 段落之间使用 &lt;p&gt; 标签分隔 (一般来说实施效果是，段落间的视觉空隙为一倍 line-height)。段首不要空格。
- 不要使用「。。。」代替「……」 ，也不要使用三个英文句点「.」代替。
- 引号一律使用「」，而不是 “”。
- 严禁出现「！！」。尽量避免使用「！」。请先冷静下来再坐电脑前敲键盘。

### 遣词造句
- 对用户称呼「你」，不再使用「您」。
- 能用中文就尽量避免英文罗马字。
- 名词：一些特写的名词可以直接使用原文而不必强译为中文。例如：HTTP、TCP。
- 用主动语态，不要用被动语态。一般情况下，主动语态比被动语态更有力。
- 使用具体、明确、展示细节的词汇，能激发想象，使读者自己代入情境。「把硬币放进口袋里，他咧开嘴笑了」，远远强过「他满意地拿走了辛苦挣来的奖赏」。
- 减少形容词的使用，少用 「的」，避免使用「哈，哈哈」、「呵，呵呵」等。
- 尽量使用常用词汇，不要用网络新词、科学术语和行话，该解释的要解释清楚。
- 记住，不要让用户来猜你在写什么。
- 记住，如果你写了一条文案觉得非常聪明非常好笑，很可能需要停下来想一下用户是否能理解了。（本条感谢 37signals 的文案建议）
- 「的」「地」「得」要用对。是的，小学都不要求这个了，但是要用对。（[「的、地、得」的用法有何区别？- 知乎](https://www.zhihu.com/question/23579160)）
- 卖萌和幽默建议：
	- 以下情况下幽默卖萌需要非常谨慎：报错信息，涉及支付、安全和隐私的信息；
	- 以下情况下推荐卖萌或幽默文案：用户引导、新功能介绍。

### 用字规范
- 根据软件发布流程的一般写法，所有用户可见的版本有：Beta、Release Candidate，未来可能对开发者可见的版本：Alpha。统一为首字母大写。两侧不出现中文或英文引号，也不出现括号。
- 用 root（小写字母）直接表达 root，不用引号。
- 「USB 调试」开关
- 账号（错误：帐号，账户，帐户）
- 登录账号（错误：登陆）
- 硬盘空间（不建议使用：磁盘）

### 开源软件文案**要求**

开源、内部开源文档，需要回答如这几个问题：

- 是什么？能做什么？
- 为谁服务？
- 如何使用？
- 如何为它贡献代码 / 内容？[CONTRIBUTING.md](https://github.com/blog/1184-contributing-guidelines)
- 是否有设计 / 架构介绍



### 版权
CopyRight: 本规范引用自 [豌豆荚文案风格指](https://docs.google.com/document/d/1R8lMCPf6zCD5KEA8ekZ5knK77iw9J-vJ6vEopPemqZM/edit#)，略作修改。




