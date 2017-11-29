---
title: 面试题
---
## jsonp跨域
### 服务端
``` js
var http = require('http');
var url = require('url');

http.createServer(function(req, res) {
    res.writeHead(200, {'Content-Type': 'text/plain'});

    // 解析 url 参数
    var params = url.parse(req.url, true).query;
    // jsonpCallback 为前后端约定的字段，用于获取回调函数的名称
    res.end(params.jsonpCallback + "('This is JSONP.')");
}).listen(8888);
```

### 本地
``` js
<script>
    // 定义回调函数
    var cb = function(data) {
        var oDiv = document.getElementById('content');
        oDiv.innerHTML = data;
    }

    var url = 'http://localhost:8888?jsonpCallback=cb';

    // 创建 script 标签，并设置其 src 属性
    var script = document.createElement('script');
    script.src = url;

    // 插入 body，此时调用开始
    document.body.appendChild(script);
</script>
```

## jquery中使用jsonp
### 服务端代码不变

### 本地
``` js
var oDiv = document.getElementById('content');

// 定义回调函数
// 只是用于服务端获取名称，也可以自行实现，从而在 `success` 中进行调用
var cb = function() {};

$.ajax({
    url: 'http://localhost:8888',
    type: 'get',
    dataType: 'jsonp',  // 预期服务器返回的数据类型
    jsonp: 'A_callback',  // 指定回调查询参数的名称，即前后端约定的字段，默认为“callback"
    jsonpCallback: 'cb',  // 指定回调函数名称
    cache: true,
    success: function(data) {   // jQuery 将 JSON 数据剥离出来，传入 success 和 error
        console.log(data);  // 'This is JSONP realized by jQuery.'
        oDiv.innerHTML = data;
    }
});
```
### jsonp的缺点
JSONP 的主要缺点有两个：
一、是只能 GET 不能 POST，因为是通过<script>引用的资源，参数全都显式的放在URL里，和 AJAX 没有半毛钱关系。
二、是存在安全隐患，动态插入<script>标签其实就是一种脚本注入，XSS

### HTTP TCP/IP协议
TCP/IP分为四层：链路层，网络层，传输层，应用层
1.链路层：用于处理链接网络的硬件部分。包括控制操作系统，硬件的沈北驱动网卡，及光纤等物理可见部分，硬件上的范畴均在链路层的作用范围之内；
2.网络层：用来处理网络上流动的数据包，数据包是网络传输最小的数据单位。该层规定了通过怎样的路径到达对方的计算机，并把数据包传送给对方。
在与对方计算机进行传输时，网络层所起的作用就是在众多的选项内选择一条传输路线
3.传输层：TCP（传输控制协议） UDP（用户数据包协议）
4.应用层：FTP（文件传输协议） DNS（域名系统HTTP协议）


#### 从服务端到客户端
应用层 -> 传输层（添加TCP头部）-> 网络层 （添加IP头部）-> 链路层（添加以太网头部）

#### 客户端收到之后则一层一层删掉头部

#### IP协议的作用是在茫茫的网海中找到对方
#### TCP协议就是安全的把数据给对方，就是三次握手就是在这个协议内
#### DNS协议就如同人的记忆，当你访问过一个网站的时候，它就会把对方的IP地址记住，下次访问的时候就不用去外网服务器查找对方的IP地址了


### 对原型链的理解
每创建一个函数都会有一个prototype属性，这个属性是一个指针，指向一个对象（通过该构造函数创建实例对象的原型对象）。原型对象是包含特定类型的所有实例共享的属性和方法。原型对象的好处是，可以让所有实例对象共享它所包含的属性和方法。
使用：利用原型让一个引用类型继承另一个引用类型的属性和方法。
每个构造函数都有一个原型对象，原型对象都包含一个指向构造函数想指针(constructor)，而实例对象都包含一个指向原型对象的内部指针(__proto__)。
```js
function animals(){}
// animals.prototype.constructor  指向函数本身
var a1 = new animals();
a1.__proto__ === animals.prototype;  // true
```

### 快速排序
```js
function sortA(arr){
    // 如果只有一位，就没有必要比较
    if(arr.length<=1){
        return arr;
    }
    // 获取中间值的索引
    var len = Math.floor(arr.length/2);
    // 截取中间值
    var cur = arr.splice(len,1);
    // 小于中间值放这里面
    var left = [];
    // 大于的放着里面
    var right = [];
    for(var i=0;i<arr.length;i++){
        // 判断是否大于
        if(cur>arr[i]){
            left.push(arr[i]);
        }else{
            right.push(arr[i]);
        }
    }
    // 通过递归，上一轮比较好的数组合并，并且再次进行比较。
    return sortA(left).concat(cur,sortA(right));
}
```
