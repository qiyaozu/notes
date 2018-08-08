---
title: js相关
---

### 命名空间 作用：避免全局污染
```js
(function () {
    var _NS = function () {}

    _NS.prototype.html = function (obj,value) {
        var isArray=this.isArrayLike(obj), i=0;

        if (typeof value == 'string') {
            if (!isArray) {
                obj.innerHTML = value;
            } else {
                var length = obj.length;
                while (i < length) {
                    obj[i].innerHTML = value;
                    i += 1;
                }
            }
        } else {
            if (!isArray) {
                return obj.innerHTML;
            } else {
                return obj[0].innerHTML;
            }
        }
    }

    window.NS = new _NS();
})();
```

### js常用库函数的npm
1.在当前项目下安装
```
npm install --save-dev outils
```

2.按需引入
```js
const getOS = require('outils/getOS')
const OS = getOS()
```

### 获取一个字符串的字节长度
```js
function GetBytes(str) {
  var len = str.length;
  for (var i = 0; i < len; i++) {
      //console.log(str[i],str.charCodeAt(i));
      if (str.charCodeAt(i) > 255) len++;
  }
  return len;
}
```

### 求一个数组的最大值
  Math.max.apply(null, arr)

### 监听屏幕的变化
```js
var mql = window.matchMedia('(orientation: portrait)');
console.log(mql);

function handleOrientationChange(mql) {
        if (mql.matches) {
            console.log('portrait'); // 竖屏
        } else {
            console.log('landscape'); // 横屏
        }
    }
    // 输出当前屏幕模式
handleOrientationChange(mql);
// 监听屏幕模式变化
mql.addListener(handleOrientationChange);
```

## 安卓手机在input输入框获得焦点的时候，整个页面上移

```js
// window.onload 或者$(function() {})中添加
var u = navigator.userAgent;
  if (u.indexOf('Android') > -1 || u.indexOf('Linux') > -1) {//安卓手机
      var input = document.querySelector('input')
      input.addEventListener('focus', function () {
          setInterval(function () {
            input.scrollIntoView(true); // 核心
          }, 100)
      })
  }
```
