---
{"dg-publish":true,"permalink":"/09 - 网页剪切/Blink · Arduino入门教程——官方示例注释与分析 · 看云/","created":"2024-09-23T13:32:57.474+08:00","updated":"2024-09-23T13:32:57.474+08:00","dg-note-properties":{"page-title":"Blink · Arduino入门教程——官方示例注释与分析 · 看云","url":"https://www.kancloud.cn/yundantiankong/arduino_examples/431622","date":"2024-09-23 13:32:56"}}
---

## 闪烁的LED

> 这个例子展示了在Arduino板Genuino板上能够看到的最简单”输出”操作：让一个LED小灯闪烁。

### 所需硬件

-   Arduino或Genuino板
-   LED小灯
-   220Ω电阻

### 电路

连接**电阻**的一端到Arduino板的13号引脚，将LED较长的一端（叫作阳极，电流流入的地方）连接到电阻的另一端。   
连接LED较短的一端到Arduino GND接口。连线如下图所示。  
![](https://box.kancloud.cn/61a134c719e0c975f0250d1f1be44bb4_676x711.png)  
大多数Arduino板已经有一个板载LED灯和13引脚相连。   
如果你没有连接外部的小灯并在板上运行了这个工程，你应该可以看到板载的LED闪烁。

和LED搭配的电阻值可能并非是220Ω；LED和1kΩ以下的电阻搭配都会亮起。

### 原理图

![](https://box.kancloud.cn/cca2e650ca0fd51ab601b6ea83b53c47_452x531.png)

### 代码

在搭好电路之后，将Arduino或Genuino板插入电脑并启动Arduino IDE，然后将这段代码输入。也可从**文件>例子>01.Basics/Blink**(File/Examples/01.Basics/Blink )中找到。

代码中做的第一件事情就是将13号引脚**初始化**为**输出引脚**(OUTPUT pin)

```
pinMode(13, OUTPUT);
```

在主循环中你用这行代码打开LED：

```
digitalWrite(13, HIGH);
```

这行代码给13号引脚加了5V的电压。这个操作使得LED两侧产生电压差，并且由此点亮了LED。接着你用以下代码把LED关闭:

```
digitalWrite(13, LOW);
```

这行代码将13号引脚重新置为了0V的低电压，以此关掉了LED。

LED开与关是及其迅速的，而你是想让人们有足够时间来看到这个改变。因此就要用delay()函数告诉板子：你等着别动，1000毫秒（就是1秒）后再继续。当你看到delay()出现时就意味着在这个时间内什么都不做。

在你了解了基本例子之后再看一下02.Digital 数字引脚操作 BlinkWithoutDelay 不用delay函数闪烁led ，它会展示如何在delay的过程中同时做其他事情。

```
/*
  点亮LED
  将LED点亮一秒钟，接着熄灭一秒钟，不断重复这一过程。

  大多数Arduino都有一个可控的板载LED，Uno和Leonardo板就有一个与13号引脚连接的LED。如果不确定你的Arduino上哪个引脚连接着板载LED
  看看这个网址：http://www.arduino.cc

  示例代码是公开的
  */

//setup函数在重新上电或按了复位后只运行一次
void setup() {
  // 初始化13引脚，并将其定义为输出引脚。
  pinMode(13, OUTPUT);
}

// loop函数永远地重复执行
void loop() {
  digitalWrite(13, HIGH);   // 将LED点亮（HIGH代表高电压）
  delay(1000);              // 停一秒钟
  digitalWrite(13, LOW);    // 将LED熄灭（LOW代表低压）
  delay(1000);              // 停一秒钟
}
```

## 相关资料

[setup()](http://www.arduino.cc/en/Reference/Setup)  
[loop()](http://www.arduino.cc/en/Reference/Loop)  
[pinMode()](http://www.arduino.cc/en/Reference/PinMode)  
[digitalWrite()](http://www.arduino.cc/en/Reference/DigitalWrite)  
[delay()](http://www.arduino.cc/en/Reference/Delay)  
读取模拟信号、串口操作   
Arduino工程的最小单元   
读取数字引脚   
LED亮度渐隐   
读取模拟电压