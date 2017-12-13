---
title: vue学习
---

### 过滤器可以用在两个地方：mustache 插值和 v-bind 表达式。
>注：mustache是指标签之间

## 计算属性可以缓存  优化的时候可以用到
### 复杂的数据变化，应该使用计算属性
### 运行 vm.fullName = 'John Doe' 时， setter 会被调用， vm.firstName 和 vm.lastName 也相应地会被更新。
```js
computed: {
  fullName: {
    // getter
    get: function () {
      return this.firstName + ' ' + this.lastName
    },
    // setter
    set: function (newValue) {
      var names = newValue.split(' ')
      this.firstName = names[0]
      this.lastName = names[names.length - 1]
    }
  }
}
```

### 自己写一个过滤器
```js
new Vue({
  filters: {
    capitalize: function (value) {
      if (!value) return ''
      value = value.toString()
      return value.charAt(0).toUpperCase() + value.slice(1)
    }
  }
})
```

### vue项目引入阿里云图标字体
1.在static目录下创建icon文件夹
2.把阿里云下载的压缩文件解压，把有用的文件放到icon目录下
3.在index.html页面引入iconfont.css
4.在浏览器打开demo_fontclass.html,查看相关的class
5.在页面中使用<i class="iconfont icon-xxx"></i>


### 路由传参的方式
```js
// 这种传参不会显示在url中，但是收到的页面刷新以后，数据会丢失
this.$router.push({name: '/index', params: {
  id: 000,
  count: 9
}})
// 这种会在url中经过encode编码后传过去，数据格式会改变，传之前最后JSON.stringify转化
this.$router.push({name: '/index', query: {
  id: 000,
  count: 9
}})
```

### dom操作
> created要进行dom操作就要放到this.$nextTick(() => {
>   // function
> })函数中

### 小型项目不用vuex，进行兄弟页面之间的传参，使用eventBus，实际使用中出现出发多次的bug
1.在src目录下创建一个bus.js
```js
import Vue from 'vue';
export default new Vue();  
```
2.在要传参的页面和接受参数的页面引入bus.js
3.点击的时候，调用toBus
```js
let data = 'faljdlal';
toBus() {
  Bus.$emit('getTarget', data);
  this.$router.push('/my')
},
```
4.接收页面，created 函数里面添加
```js
  Bus.$on('getTarget', target => {  
    console.log(target);  
 });  
```

### vue项目中使用typescript
1.安装TypeScript相关依赖和项目其余依赖，用npm或cnpm
```
npm install typescript ts-loader --save-dev
```
2.修改目录下bulid/webpack.base.conf.js文件，在文件内module>rules添加以下规则
```
{
  test: /\.tsx?$/,
  loader: 'ts-loader',
  exclude: /node_modules/,
  options: {
    appendTsSuffixTo: [/\.vue$/],
  }
},
```
3.在src目录下新建一个文件vue-shims.d.ts，用于识别单文件vue内的ts代码
```js
declare module "*.vue" {
  import Vue from "vue";
  export default Vue;
}
```
4.在项目根目录下建立TypeScript配置文件tsconfig.json
```js
{
  "compilerOptions": {
    "strict": true,
    "module": "es2015",
    "moduleResolution": "node",
    "target": "es5",
    "allowSyntheticDefaultImports": true,
    "lib": [
      "es2017",
      "dom"
    ]
  }
}
```
5.
重命名src下的main.js为main.ts

修改webpack.base.conf.js下的entry>app为'./src/main.ts'

修改src下的App.vue文件
```js
<script lang="ts">
```

### 遇到横竖屏的情况，better-scroll无法准确计算content的高度，better-scroll的div高度不能用100%，用100vh

### 最近vue项目无法在局域网中访问，解决方案： host：0.0.0.0   nuxt项目同样适用

### vue项目url中取消#，在路由文件中添加:  mode: 'history'
```js
const router = new VueRouter({
  mode: 'history',
  routes:[
    {
      path: '/video',
      name: 'video',
      component: Video,
      meta:{
        verify: true
      }
    }
  ]
});
```

### 打包之后的js、css文件路径问题解决  webpack.base.conf.js
```js
output: {
  path: config.build.assetsRoot,
  filename: '[name].js',
-  publicPath: process.env.NODE_ENV === 'production'
-   ? config.build.assetsPublicPath
-    : config.dev.assetsPublicPath
+  publicPath: './'或者''
},
```

### 打包之后的背景图片的路径会找不到，so，如果用到背景图片的话，最好放到assics目录下

### vue项目在vscode下使用eslint，最好在生成项目的时候就安装eslint，配置.eslintrc.js
> 需要安装两个插件
```
cnpm install eslint-plugin-html eslint-plugin-vuefix -D
```
```js
plugins: [
    'vuefix'      // 这里需要修改一下
  ],
  // add your custom rules here
  rules: {
    "vuefix/vuefix": [2, {"auto": true}]      // 这里直接粘贴过去，也没人给解释，在保存vue文件的时候，就会自动格式化，个人认为比较方便
  }
```