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