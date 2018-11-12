---
title: react native
---

# React Native学习

## 总的一句话，因为你RN的社区比较完善（相对于weex），所以打算深入的学习一下，下面就是所有的采坑过程

### 1.首先就是在Mac上运行react-native run-ios会出现：No bundle URL present

解决办法是： 在 /etc/hosts文件夹下面添加：
```code
127.0.0.1           localhost
255.255.255.255      broadcasthost
```

### Mac下ios的调试，在那个手机界面按CMD + D，会出现Remote Js Debugger,点击了之后就可以在localhost:8081/debugger-ui页面，打开开发者调试 -> sources -> debuggerWorker.js

### Image不显示的问题，可能是因为图片uri的地址不是png或者jpg结尾的格式

### Button样式不生效，需要在外层添加一层view，设置view的样式即可

### 最新版的react native想要密码输入框，添加下面的属性：

```code
secureTextEntry={true}
```

### ios 打开调试： CMD + ctrl + z

