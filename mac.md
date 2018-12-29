---
title: MAC 相关
---
# MAC 相关

## Mac清理命令

  sudo periodic daily

## MAC查看隐藏文件的快捷键 cmd + shift + .

## 把下面的内容添加进去即可

JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk1.8.0_131.jdk/Contents/Home

CLASSPAHT=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar

PATH=$JAVA_HOME/bin:$PATH:

export JAVA_HOME

export CLASSPATH

export PATH

## Mac 升级node到最新稳定版

> 在全局安装node的版本管理工具  ： n

  npm install -g n

> sudo 是必须的，latest是最新版，stable是最新稳定版

  n latest

  n stable

## mac使用wireshark进行抓包， 因为布吉岛青花瓷怎么抓取安卓端的数据

若运行 wireshark.app 弹窗提示“You don't have permission to capture on that device”：
> sudo wireshark    // 亲测有效

wireshark界面的每个部分详细介绍： https://www.jianshu.com/p/62f00db7be68

## mac使用charles进行手机代理，

1.先到微云或者百度云去安装charles
2.proxy -> Proxy setting 查看http代理的端口是否是8888
3.保证手机端和mac在一个局域网下面
4.iphone端需要安装一个插件， 下载Charles证书http://www.charlesproxy.com/ssl.zip 发送给自己，点击安装即可，(2) 在手机浏览器中访问地址：http://charlesproxy.com/getssl，即可打开证书安装的界面
5.安卓端就直接修改http的代理设置，主机名为mac的ip地址，端口是8888， iphone一样
6.移动端配置好之后，charles会询问是否允许某个ip进行代理，选择allow即可
7.想要抓取那个服务器的包，proxy -> recording Setting -> Include -> Add -> 填写相关域名 -> OK
8.https://www.cnblogs.com/dsxniubility/p/4621314.html 详细介绍
9.打断点： 在想要打断点的链接上右键  breakpoint 然后请求这个接口 charles会自动打开可编辑请求的界面  底部有个execute按钮，就是提交的意思；接下来能看到刚刚提交的那个接口箭头朝下了，这样就可以对返回的数据进行编辑了
10.  http://blog.csdn.net/LVXIANGAN/article/details/70599580 详细使用

## wget使用

>> 下载文件并命名

  wget -O wordpress.zip http://www.linuxde.net/download.aspx?id=1080

>> 限速下载

  wget --limit-rate=300k http://www.linuxde.net/testfile.zip

>> 使用wget断点续传

  wget -c http://www.linuxde.net/testfile.zip

>> 使用wget后台下载

  wget -c http://www.linuxde.net/testfile.zip
  tail -f wget-log    // 查看进度

>> 伪装代理名称下载

  wget --user-agent="Mozilla/5.0 (Windows; U; Windows NT 6.1; en-US) AppleWebKit/534.16 (KHTML, like Gecko) Chrome/10.0.648.204 Safari/534.16" http://www.linuxde.net/testfile.zip

>> 镜像网站  下载整个网站到本地。

  wget --mirror -p --convert-links -P ./LOCAL URL

>> 爬取一个网站，并可以在本地预览

  wget -c -r -npH -k http://v4.bootcss.com

**参数说明**
-c：断点续传 
-r：递归下载 
-np：递归下载时不搜索上层目录 
-nd：递归下载时不创建一层一层的目录,把所有文件下载当前文件夹中 
-p：下载网页所需要的所有文件(图片,样式,js文件等) 
-H：当递归时是转到外部主机下载图片或链接 
-k：将绝对链接转换为相对链接,这样就可以在本地脱机浏览网页了

* --miror开户镜像下载。
* -p下载所有为了html页面显示正常的文件。
* --convert-links下载后，转换成本地的链接。
* -P ./LOCAL保存所有文件和目录到本地指定目录

## mac文件路径添加到系统环境变量

>> 将anaconda的bin目录加入PATH，根据版本不同，也可能是~/anaconda3/bin

  echo 'export PATH="~/anaconda2/bin:$PATH"' >> ~/.bashrc

>> 更新bashrc以立即生效

  source ~/.bashrc  

### mac terminal打开软件 或者用finder打开指定的目录

  open -a Safari touch.html
  open -a finder /usr/local/etc/nginx

### 使用ngrok将本地端口映射到外网给别人看

1. [下载软件](https://ngrok.com/download)
2. 把软件解压
3. 把本地项目跑起来, 假如端口是8080
4. 假如我下载在Download文件夹， cd Download
5. ngrok http 8080
6. forwarding后面就是外网的地址
7. 需要注意的是新版本的webpack出于安全考虑，默认检查hostname，如果hostname不是配置内的，将中断访问。
  
处理方式是： 在webpack.dev.conf.js 找到devServer对象里面添加

```js
disableHostCheck: true
```

这种方式映射到外网，会出现本地图片显示不出来
比较好的方式是先打包一下，然后用python跑起来，把python端口映射出去即可
自己的id： ./sunny clientid 956b67e3d71bc6fd

### [卫星地图](http://www.265.me/)

### MAC上使用剪切复制

  cmd + c 复制
  cmd + option + v 移动   注：必须要在mac键盘上按   外接键盘没反应

### MAC上卸载输入法要先下载输入法安装包，然后再进行卸载

### 看html5视频没有快进？？试试谷歌的这款插件吧 html5 video speed controller(需要翻墙安装)，安装完成之后，看视频就会在左上角看到有个1.0， 鼠标移动上去就可快进

### MAC上命令行听歌 [github地址](https://github.com/darknessomi/musicbox)

### 查看端口占用情况，并杀死
```code
sudo lsof -i tcp:port

sudo kill -9 PID
```

## mac下谷歌浏览器解决跨域： （前提是要在*Documents*文件夹下面创建*MyChromeDevUserData*空目录，**下面的用户名也记得改一下**）
  open -n /Applications/Google\ Chrome.app/ --args --disable-web-security  --user-data-dir=/Users/yaozu/Documents/MyChromeDevUserData 
