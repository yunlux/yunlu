---
{"dg-publish":true,"permalink":"/09 - 网页剪切/Arduino Nano V3.0改进版 开箱晒物_键盘_什么值得买/","created":"2024-09-23T13:33:01.917+08:00","updated":"2024-09-23T13:33:01.918+08:00"}
---

## Arduino Nano V3.0改进版 开箱晒物

2019-10-05 23:10:36 19点赞 74收藏 29评论

## 前言

最近制作机械[键盘](https://www.smzdm.com/fenlei/jianpan/)的过程中，发现Arduino uno可以通过刷固件实现虚拟键盘串口通讯。可是Arduino uno的体积过大，塞到键盘[外壳](https://www.smzdm.com/ju/sp11vmp/)里面并不合适。而Arduino uno的迷你版——Arduino Nano就显得很合适了。  

[![Arduino Nano V3.0改进版 开箱晒物](https://qnam.smzdm.com/201910/05/5d98829692bdd5270.jpg_e1080.jpg)](https://post.smzdm.com/p/a07o2x09/pic_2/)

## 外观展示

Arduino nano作为Arduino uno的简配版，芯片一样使用的是Atmega328p控制器。区别在于去掉了DC支流[电源](https://www.smzdm.com/ju/s2w5m72/)输入部分，USB-B型接口也替换成了Mini usb接口。  

[![Arduino Nano V3.0改进版 开箱晒物](https://qnam.smzdm.com/201910/05/5d98814b34534429.jpg_e1080.jpg)](https://post.smzdm.com/p/a07o2x09/pic_3/)

没有了DC电源输入部分，Arduino nano的尺寸变得更小，长43.18mm，宽15.24mm，重量仅仅是7g。这个尺寸与重量，塞进机械键盘外壳里面完全没有问题。  

[![Arduino Nano V3.0改进版 开箱晒物](https://qnam.smzdm.com/201910/05/5d98829fa2e7f4296.jpg_e1080.jpg)](https://post.smzdm.com/p/a07o2x09/pic_4/)

芯片为Atmega328p，带有3[2K](https://pinpai.smzdm.com/224578/)

B的Flash Memory[闪存](https://www.smzdm.com/ju/s2yly5p/)，其中的0.5kb是bootloader系统引导占用。

[![Arduino Nano V3.0改进版 开箱晒物](https://am.zdmimg.com/201910/05/5d98814acbab81943.jpg_e1080.jpg)](https://post.smzdm.com/p/a07o2x09/pic_5/)

工作电压是5伏特，Raw接口支援6-20伏特输入，IO接口的电流为40毫安。

[![Arduino Nano V3.0改进版 开箱晒物](https://am.zdmimg.com/201910/05/5d98814c02aff7925.jpg_e1080.jpg)](https://post.smzdm.com/p/a07o2x09/pic_6/)

板子上带有一个Reset重置按键，方便在刷固件时不必另外找镊子短接GND和RST接口。  

[![Arduino Nano V3.0改进版 开箱晒物](https://am.zdmimg.com/201910/05/5d98814c858c45743.jpg_e1080.jpg)](https://post.smzdm.com/p/a07o2x09/pic_7/)

接口为Mini usb接口。  

[![Arduino Nano V3.0改进版 开箱晒物](https://am.zdmimg.com/201910/05/5d98814c2082b5853.jpg_e1080.jpg)](https://post.smzdm.com/p/a07o2x09/pic_8/)

尾部还有一个ISP编程接口。

[![Arduino Nano V3.0改进版 开箱晒物](https://am.zdmimg.com/201910/05/5d98814cc218a6218.jpg_e1080.jpg)](https://post.smzdm.com/p/a07o2x09/pic_9/)

背部一样贴有原件。  

[![Arduino Nano V3.0改进版 开箱晒物](https://am.zdmimg.com/201910/05/5d98814d4a70b5855.jpg_e1080.jpg)](https://post.smzdm.com/p/a07o2x09/pic_10/)

官方原版使用的是FT232RL芯片，手头上这个华强北出品使用的则是廉价的CH340芯片。

[![Arduino Nano V3.0改进版 开箱晒物](https://qnam.smzdm.com/201910/05/5d98814da20b81854.jpg_e1080.jpg)](https://post.smzdm.com/p/a07o2x09/pic_11/)

另外还有一颗AMS1117电压转换芯片，针对。  

## 使用感受

看中Arduino Nano的优势就是IO数量，对于制作全尺寸104按键的机械键盘，至少要使用21个IO接口。  

[![Arduino Nano V3.0改进版 开箱晒物](https://qnam.smzdm.com/201910/05/5d98814ae77a25458.jpg_e1080.jpg)](https://post.smzdm.com/p/a07o2x09/pic_12/)

Arduino Nano带有14个数字接口，8个模拟接口，6个PWM接口。根据原理图中，能适用于制作机械键盘的IO接口就有22个，完全满足需求。

[![Arduino Nano V3.0改进版 开箱晒物](https://qnam.smzdm.com/201910/05/5d9882a57b14a5368.png_e1080.jpg)](https://post.smzdm.com/p/a07o2x09/pic_13/)

一般而言，Arduino Nano使用的是Arduino开发套件。在选项中，类型为Arduino nano，芯片为Atmega328p，选对端口，就能对Arduino nano进行固件烧录。  

[![Arduino Nano V3.0改进版 开箱晒物](https://qnam.smzdm.com/201910/05/5d98899f259ee5271.jpg_e1080.jpg)](https://post.smzdm.com/p/a07o2x09/pic_14/)

而制作机械键盘，我习惯于使用QMK Toolbox。在kbfirmware制作编译好hex文件，芯片类型选Atmega328p，就能成功烧录固件。  

[![Arduino Nano V3.0改进版 开箱晒物](https://am.zdmimg.com/201910/05/5d988a41e82037436.jpg_e1080.jpg)](https://post.smzdm.com/p/a07o2x09/pic_15/)

## 总结

华强北产的Arduino Nano板子，CH340芯片的价格普遍在20元左右，而FT232RL芯片的普遍价格在30元左右。一些进口芯片的会贵点，但耐用些。但是都比teensy 2.0的价格便宜，IO接口也不少，制作机械键盘也够用，对于外设党来说算是一款性价比不错的键盘主控板子。另外还有一款DFRobot推出的改进版Bluno nano，集成蓝牙4.0模块，对制作蓝牙机械键盘也不错。  

![](https://res.smzdm.com/pc/pc_shequ/dist/img/the-end.png)