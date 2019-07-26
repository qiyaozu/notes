---
title: python 学习
---
# python 学习

## Python搭建简易的服务器   前提是已经安装了python

1.在任意位置创建一个文件夹  进入
2.执行命令：python -m SimpleHTTPServer
 后面可以跟上想要的端口   不写的话  默认是8000
3.把自己的文件放到这个文件夹里面   例如：test.html
4.打开浏览器firefox 输入localhost:8000/test.html
5.python3的写法： python3 -m http.server 8080

### python爬虫步骤

https://www.liaoxuefeng.com/api/ref/001432004374523e495f640612f4b08975398796939ec3c000/topics?page=1

### pip3升级

  pip3 install --upgrade pip

### python项目运行：把所有的依赖写到以txt文件里面  

  pip install -r requirements.txt

### python虚拟环境 作用是为了和全局的环境分隔开

>> 安装

  pip install virtualenv

>> 创建虚拟环境目录

  virtualenv venv　　#venv为虚拟环境目录名，目录名自定义

>> 激活环境

  source venv/bin/activate

>> 退出虚拟环境

  source deactivate

## is 和 == 的区别
is: 判断两个对象在内存中的存储位置是否一样
==： 判断两个值是否相等 

## 在外界访问私有属性和方法： _类名__私有属性/方法

## 类的继承：
  class Animal:
    def eat(self):
      print('eat')

  class Dog(Animal):
    def bark(self):
      print('wangwang')

## 对父类方法的重写：只需要在子类的里面定义一个同名的方法即可

## 对父类方法的扩展： 在Dog的方法里面：super().eat()

## 定义类属性，以及访问类属性的注意事项
```pyhton
class Animal:
    count = 0
```
访问类属性可以Animal.count 也可以用实例化的对象去访问count，一定要用前者

## 定义类方法
```pyhton
class Animal:

    count = 0

    @classmethod
    def classmethod(cls):

      print('%s' % cls.count)


# 调用类的方法
Animal.classmethod()
```
定义类方法需要注意两个事项：
1. 定义方法之前 @classmethod
2. 方法的第一个参数是cls   class的缩写

## 静态方法: 既不需要访问类属性，也不需要访问实例属性
```pyhton
class Animal:

    count = 0

    @staticmethod
    def staticmethod():

      print('i am static method')


# 调用类的方法
Animal.staticmethod()
```

## Python爬虫利器二之Beautiful Soup的用法，[看这里](https://cuiqingcai.com/1319.html)

## 朗读文本库：pyttsx3 在mac环境下需要安装：pyobjc 这个库，不然会报Foundation module找不到

## 更改python3的链接，前提是你已经安装了python3.6

```code
alias python3="/Library/Frameworks/Python.framework/Versions/3.6/bin/python3.6"
```

## opencv for mac安装教程：
> 参考的是[这个链接，需要翻墙](https://www.learnopencv.com/install-opencv3-on-macos/)
```code
brew install python3
brew link pyhton3
brew install opencv // 这里我安装的是4
ln -s /usr/local/opt/opencv@4/lib/python3.7/site-packages/cv2/python3.7/cv2.cpython-37m-darwin.so cv2.so
pip3 install numpy scipy matplotlib scikit-image scikit-learn ipython pandas opencv-python
```

## brew想安装指定的版本软件

1. 百度了一下，看了好几篇文章：https://www.jianshu.com/p/e47fc32060e6?utm_source=oschina-app，这篇文章说的还比较详细一点
2. 因为我已经换了brew的源，所以git log python.rb,根本看不到python3.6和python3.5的id（我用的是清华源）
3. 接下来是我自己的步骤：
* 从：https://www.python.org/downloads/mac-osx/ 下载指定的版本，python这个东西还是不要尝新，我现在换回了3.5的版本
* pkg安装的默认目录是：/Library/Frameworks/Python.framework/Versions/3.5/bin/python3
* mv /Library/Frameworks/Python.framework/Versions/3.5/bin/python3 /usr/local/bin/
* 记得把.bash_profile里面的路径也改一下，source一下

## 因为先用brew安装了python3，版本过高，就用下载pkg的方式去安装，安装好了之后，使用pip3 install 。。不会安装到当前版本的库中，下面是解决方式，感觉会有更好的解决方式，如果你知道，麻烦分享一下，1640644790@qq.com！一起进步
```
python3 -m pip install itchat
```
