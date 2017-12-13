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


