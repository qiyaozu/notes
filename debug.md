---
title: 调试的小技巧
---

### console.table   ：可以把对象以表格的形式输出
```javascript
var animals = [
    { animal: 'Horse', name: 'Henry', age: 43 },
    { animal: 'Dog', name: 'Fred', age: 13 },
    { animal: 'Cat', name: 'Frodo', age: 18 }];
 console.table(animals);
```
### console.counts()   可以查看某个函数的调用次数

### 在代码里面添加 `debugger;`可以进行断点调试

### Object.keys(obj)   返回：obj的所有key组成的数组

### Object.values(obj)  返回：obj的多有value组成的数组
