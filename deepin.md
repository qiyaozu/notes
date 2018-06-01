---
title: deepin linux 的快速使用（双系统）
---

### 1. 下载系统
```
https://www.deepin.org/download/
```

### 2.制作启动盘，启动盘制作工具（window）
```
http://cdimage.deepin.com/applications/deepin-boot-maker/windows

```
如何制作：https://www.deepin.org/original/deepin-boot-maker/

### 3. 如果系统只有一个盘，记得先分一个区出来
### 4. 系统装好之后，进window系统会出现时间显示不准确，解决：
1. sudo apt-get install ntpdate
2. sudo ntpdate time.windows.com
3. sudo hwclock --localtime --systohc

### 5. 进系统之后，如果出现window盘是只读模式，那是因为你的电脑开启了快速启动，需要进boot把快速启动关闭掉即可，如果是win7的话不存在这个事，win7没有快速启动，win8、win10开启快速启动之后，硬盘并没有休眠

### 6. 装好的新系统，好多文件夹只能读，没法修改
```
sudo chmod 777 /file_dir
```

### 


### 如果在网上下载的.deb安装包没法安装，有可能是在深度软件里面安装过了，要先把之前的软件卸载掉，才能安装
