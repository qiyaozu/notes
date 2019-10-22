---
title: arachni对网站进行安全检查
---

### 第一步：安装
可以从[官网](https://www.arachni-scanner.com/)去下载（下载很慢），我放了一份在百度云，使用[BND2](https://github.com/b3log/baidu-netdisk-downloaderx?utm_source=hacpai.com)去下载
网盘地址：链接: https://pan.baidu.com/s/1dioWcTHx5qR6ffMwS8l-zA 提取码: aqfm

下载完成后，解压并进入到bin目录，命令行执行：./arachni_web
![图片](/img/arachni1.png)

在浏览器打开：localhost:9292

需要输入用户名和密码

```
# 管理员账户：
账户: admin@admin.admin
密码： administrator

# 普通用户：
账户：user@user.user
密码： regular_user
```

登录成功之后：
![image](/img/arachni2.png)

输入要测试的URL，稍等片刻
![image](/img/arachni3.png)
从上图可以看出网站需要优化的地方
