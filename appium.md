---
title: appium 搭建时候用到的资料
---

appium的作用：表面上是测试ios和安卓应用，实际上可以做各种有趣的事情，比如：薅羊毛~

### 查看本机可用的虚拟设备(ios)
    xcrun simctl list devices

### 查看可用的模拟器SDK：
    xcodebuild -showsdks

### 安装fbsimctl：
    brew tap facebook/fb
    brew install fbsimctl --HEAD

### 安装fbsimctl不成功，可以参考：
    https://github.com/facebook/homebrew-fb/pull/23
    # 主要的操作：
    cd  /Users/这里要换成你的电脑名称/Library/Caches/Homebrew/fbsimctl--git
    ./build.sh fbsimctl build /usr/local/Cellar/fbsimctl/HEAD-9911af8

### 安装applesimutils：
    brew tap wix/brew
    brew install wix/brew/applesimutils

### 检测ios/android的运行环境：
    appium-doctor --ios / appium-doctor --android

### 安装opencv4nodejs
    brew install cmake
    brew install opencv@3
    echo 'export PATH="/usr/local/opt/opencv@3/bin:$PATH"' >> ~/.bash_profile
    cd ~ && source .bash_profile
    cnpm i -g opencv4nodejs

### 获取apk的包名和activityname：
    https://blog.csdn.net/xiaosongbk/article/details/82903148

### 查看安卓可用的虚拟设备：
    adb devices