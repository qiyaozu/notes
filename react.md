---
title: react 学习使用
---

### 1. 有状态组件和无状态组件的区别

### 2. 组件的渲染和传参

### 3. 行内样式的写法
```
style={{fontSize: '20px', color: 'red', zIndex: 3}}
```

### 项目里面使用less


### css模块化的配置和使用
1. 配置：
修改webpack.config.js,module -> rules -> css-loader改为css-loader?modules&localIdentName=[path][name]-[local]-[hash:6]
> 需要注意的是：模块化只针对class和id 

2. 使用：
创建css文件，CommentList.css 内容：
```css

.title {
    font-size: 15px;
    color: #e5e5e5;
}

/* 如果不想让某个class被模块化，使用下面的写法，不知道有没有小伙伴感觉这种写法很麻烦  哈哈 */
:global(.test) {
    background: #0f0;
}

```

```js
// 注意.css后缀名不能省略
import styles from '@/css/CommentList.css'
render () {
    return <div>
        <h1 className={styles.title}></h1>
    </div>
}
```


### 让代码注释可折叠
```js
//#region 这里面全部都是代码注释
// 这里面都是注释了的代码
//#endregion
```

### react中input传值
- 方法1：在onChange里面把e传进来  e.target.value
- 在input标签上绑定ref属性，this.refs.nameInput.value
