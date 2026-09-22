---
{"dg-publish":true,"permalink":"/09 - 网页剪切/Arduino + 按键开关实现简单的计数器 – Arduino 实验室/","created":"2024-09-16T00:53:12.010+08:00","updated":"2026-08-15T07:57:33.360+08:00","dg-note-properties":{"page-title":"Arduino + 按键开关实现简单的计数器 – Arduino 实验室","url":"https://arduino.nxez.com/2018/07/07/arduino-pushbutton-switch-for-simple-counter.html?variant=zh-cn","date":"2024-09-16 00:54:51"}}
---

本实验用以下材料，简单实现一个按键次数的计数器，统计按键被按下的次数，现实在串口输出栏。  
所用材料：  
Arduino UNO电路板（1块）  
面包板（1块）  
10k电阻（1个）  
按键开关（1个）  
面包线（3根）

按照下图方式将元件和Arduino连接起来。  
在 Arduino IDE 中新建一个代码文件，输入下面的代码。代码的功能看注释就好了。

1

2

3

4

5

6

7

8

9

10

11

12

13

14

15

16

17

18

19

20

21

22

23

24

25

26

27

28

29

30

31

32

33

34

35

36

37

38

39

40

41

42

43

44

45

46

47

48

49

50

51

52

53

54

55

56

57

58

59

60

61

62

63

64

65

66

const int&nbsp; buttonPin = 2;

const int ledPin = 13;

int buttonPushCounter = 0;

int buttonState = 0;

int lastButtonState = 0;

void setup() {

&nbsp;&nbsp;pinMode(buttonPin, INPUT);

&nbsp;&nbsp;pinMode(ledPin, OUTPUT);

&nbsp;&nbsp;Serial.begin(9600);

}

void loop() {

&nbsp;&nbsp;buttonState = digitalRead(buttonPin);

&nbsp;&nbsp;if (buttonState != lastButtonState) {

&nbsp;&nbsp;&nbsp;&nbsp;if (buttonState == HIGH) {

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;buttonPushCounter++;

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Serial.println("on");

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Serial.print("number of button pushes:&nbsp; ");

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Serial.println(buttonPushCounter);

&nbsp;&nbsp;&nbsp;&nbsp;} else {

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Serial.println("off");

&nbsp;&nbsp;&nbsp;&nbsp;}

&nbsp;&nbsp;&nbsp;&nbsp;delay(50);

&nbsp;&nbsp;}

&nbsp;&nbsp;lastButtonState = buttonState;

&nbsp;&nbsp;if (buttonPushCounter % 4 == 0) {

&nbsp;&nbsp;&nbsp;&nbsp;digitalWrite(ledPin, HIGH);

&nbsp;&nbsp;} else {

&nbsp;&nbsp;&nbsp;&nbsp;digitalWrite(ledPin, LOW);

&nbsp;&nbsp;}

}

然后上传代码到 Arduino，并打开串口调试窗口（放大镜图标）。

效果就是，当你每次按下或松开按键开关，都会打印相应的字符串，来显示当前的按键状态。而与此同时，Arduino UNO上的LED，也会在你每按四次按键更新一次状态。

9,992

[](https://talk.quwj.com/node/arduino "趣小组-Arduino")

  

-   [arduino](https://arduino.nxez.com/tag/arduino)
-   [level2](https://arduino.nxez.com/tag/level2)
-   [开关](https://arduino.nxez.com/tag/%e5%bc%80%e5%85%b3)
-   [按键开关](https://arduino.nxez.com/tag/%e6%8c%89%e9%94%ae%e5%bc%80%e5%85%b3)
-   [教程](https://arduino.nxez.com/tag/%e6%95%99%e7%a8%8b)