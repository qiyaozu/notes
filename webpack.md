---
titie: webpack
---

# nuxt项目无法在本机ip下访问， 在package.json文件下添加,注：config是和script是同一级的

```js
"config": {
    "nuxt": {
        "host": "0.0.0.0",
        "port": "3000"
    }
  },
```

## SPA无法在本机ip下访问,同样是在package.json文件下,在script -> dev 添加：--host 本机IP

```js
"scripts": {
  "dev": "webpack-dev-server --inline --progress --config build/webpack.dev.conf.js --host 192.168.1.127",
  "start": "npm run dev",
  "lint": "eslint --ext .js,.vue src",
  "build": "node build/build.js"
},
```
