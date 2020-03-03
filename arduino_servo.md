---
title: arduino servo电机的使用，以及注意事项
---

## 如何使用：
1. 三条线的理解
* 红色连接5v
* 棕色连接GND
* 橘黄色连接模拟讯号接口（只能连接带波浪线的）

## arduino软件中使用：
```code c++

// 引入操作库
#include <Servo.h>

// 给要操作的servo电机命名
Servo myservo;  // create servo object to control a servo

void setup() {
    // 连接9号接口
  myservo.attach(9);  // attaches the servo on pin 9 to the servo object
}

void loop() {
    // 旋转180度
  myservo.write(180);                  // sets the servo position according to the scaled value
  delay(15);                           // waits for the servo to get there
}

```