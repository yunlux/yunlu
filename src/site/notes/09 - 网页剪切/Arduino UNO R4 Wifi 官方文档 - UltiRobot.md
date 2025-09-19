---
{"dg-publish":true,"permalink":"/09 - 网页剪切/Arduino UNO R4 Wifi 官方文档 - UltiRobot/","created":"2024-09-26T19:08:33.677+08:00","updated":"2024-09-26T19:08:33.678+08:00"}
---

## Arduino UNO R4 WiFi 开发板

官方原文地址：[英文文档](https://docs.arduino.cc/tutorials/uno-r4-wifi/cheat-sheet)

Arduino UNO是我们最受欢迎且在全球范围内得到认可的开发板，自发布以来，它已成为制造者社区和教育界的重要组成部分。Arduino UNO R4 WiFi开发板是UNO开发板第四版的一部分，也是第一个搭载32位微控制器(MCU)的版本（来自瑞萨电子的RA4M1系列）。

本文档作为UNO R4 WiFi的技术概览，您将找到一系列资源和指南链接，帮助您开始下一个项目。

ESP32模块和瑞萨RA4M1芯片是一个复杂的USB-串行系统的一部分，它非常灵活和适应性强，以支持HID特性，同时保留编程主MCU和ESP32的能力，如果您愿意的话（尽管这是一个高级选项，需要一些技术手段）。

默认情况下，板载的ESP32模块运行的固件负责UNO R4 WiFi的连接性。您可能需要更新此固件以启用新功能，或解决漏洞和其他问题。更新这个固件有几种方法，您可以在我们的帮助中心文章中找到它们的详细信息。

您还可以访问Arduino UNO R4 WiFi的文档平台。

## 数据手册

完整的数据手册可以从下面的链接下载PDF文件：

[下载UNO R4 WiFi数据手册](https://docs.arduino.cc/resources/datasheets/ABX00087-datasheet.pdf)

## 电源供应

开发板可以通过VIN引脚供电，支持6-24V的范围。VIN引脚也连接到直流插孔（圆柱插头连接器）。

通过VIN引脚供电时，您正在使用板载调节器将电压降至5V，这意味着5V引脚可以提供高达1.2A的电流。请记住，这个电压调节器也为电路板上的其余部分供电，包括MCU、LED等组件。

外部设备（例如伺服电机）如果电流需求较大，绝不应通过5V引脚供电。它主要用于电流需求较低的设备，如传感器模块。

如果您使用USB-C®连接器，必须用5V供电。

通过USB供电时，您完全绕过了板载电压调节器。在这种情况下，5V引脚可以提供高达2A的电流，而不会损坏开发板。

## 核心

UNO R4 WiFi基于Arduino UNO R4 Core。

## 安装

UNO R4 WiFi可以通过Arduino IDE、Arduino Web Editor或Arduino CLI编程。

### Arduino IDE

要在Arduino IDE中使用这块开发板，您需要从板管理器安装最新版本的Arduino UNO R4 Boards包。

在[开始使用UNO R4 WiFi指南](https://docs.arduino.cc/tutorials/uno-r4-wifi/r4-wifi-getting-started)中了解更多信息。

### Arduino Web Editor

Web Editor是一个在线IDE，包括所有官方板，无需安装核心/包。您需要在计算机上安装Create插件才能使用Web Editor。

在[开始使用Web Editor指南](https://docs.arduino.cc/arduino-cloud/getting-started/getting-started-web-editor)中了解更多信息。

### Arduino IoT Cloud

Arduino UNO R4 WiFi与Arduino IoT Cloud兼容，这是一个云服务，允许您在短时间内创建IoT应用程序。

访问[开始使用Arduino IoT Cloud指南](https://docs.arduino.cc/arduino-cloud/getting-started/iot-cloud-getting-started)获取更多信息。

## 瑞萨RA4M1

UNO R4 WiFi采用了强大且非常稳健的瑞萨微控制器，该控制器也用于UNO R4 Minima上。瑞萨的微控制器以其高性能和稳健性而闻名，包括其内置的外设集。

这些外设包括模数转换器、定时器、脉冲宽度调制（PWM）单元、通信接口（例如UART、SPI和I2C）等。  
[![](https://arduino.me/storage/v1/object/public/image/249c3c4cdcc71ff8bae976e4b23bc2f9.webp)](https://arduino.me/storage/v1/object/public/image/249c3c4cdcc71ff8bae976e4b23bc2f9.webp)  
微控制器在UNO R4 WiFi上

## 内存

开发板特点：

-   32 kB的SRAM
-   256 kB闪存
-   8 kB数据（EEPROM）。

## 引脚

UNO R4 WiFi为您提供了许多不同的引脚，其中许多引脚具有特殊功能，这将在本文的后续部分中解释。继续阅读以了解您可以用它们做什么。

如果您只需要快速了解引脚的功能，这是UNO R4 WiFi上所有IO引脚的完整表格。

| 引脚 | 类型 | 功能 |
| --- | --- | --- |
| D0 | 数字 | UART接收 |
| D1 | 数字 | UART发送 |
| D2 | 数字 | GPIO引脚，中断 |
| D3 | 数字 | GPIO引脚，中断，PWM |
| D4 | 数字 | GPIO引脚 |
| D5 | 数字 | GPIO引脚，PWM |
| D6 | 数字 | GPIO引脚，PWM |
| D7 | 数字 | GPIO引脚 |
| D8 | 数字 | GPIO引脚 |
| D9 | 数字 | GPIO引脚，PWM |
| D10 | 数字 | SPI（CS），GPIO引脚，PWM |
| D11 | 数字 | SPI（COPI），GPIO引脚，PWM |
| D12 | 数字 | SPI（CIPO），GPIO引脚 |
| D13 | 数字 | SPI（SCK），GPIO引脚，内置LED |
| A0 | 数字 | 模拟输入，DAC |
| A1 | 模拟输入 | 模拟输入，运算放大器+ |
| A2 | 模拟输入 | 模拟输入，运算放大器- |
| A3 | 模拟输入 | 模拟输入，运算放大器输出 |
| A4 | 模拟输入 | 模拟输入，SDA\* |
| A5 | 模拟输入 | 模拟输入，SCL\* |

\*A4和A5引脚都连接到同一个I2C总线。

## 模拟引脚

UNO R4 WiFi有六个模拟输入引脚（A0-A5），可以使用analogRead()函数读取。

| 引脚 | 类型 | 功能 |
| --- | --- | --- |
| A0 | 模拟 | 模拟输入，DAC |
| A1 | 模拟 | 模拟输入，运算放大器+ |
| A2 | 模拟 | 模拟输入，运算放大器- |
| A3 | 模拟 | 模拟输入，运算放大器输出 |
| A4 | 模拟 | 模拟输入，SDA\* |
| A5 | 模拟 | 模拟输入，SCL\* |

\*A4和A5引脚都连接到同一个I2C总线。

```
value = analogRead(pin);
```

这些引脚的默认参考电压是5V，但可以如下更改：

```
analogReference(AR_DEFAULT) // 默认参考5V
analogReference(AR_INTERNAL) // 内置参考1.5V
```

默认分辨率设为10位，但可以更新为12位和14位分辨率。要这样做，请在您的草图的setup()中使用以下方法。

```
analogReadResolution(10) // 默认
analogReadResolution(12)
analogReadResolution(14)
```

要了解更多关于UNO R4 WiFi的ADC能力，请查看ADC分辨率指南。

## 运算放大器引脚

RA4M1有一个内部运算放大器，在UNO R4 WiFi上如下公开：

| 引脚 | 运算放大器 |
| --- | --- |
| A1 | 运算放大器+ |
| A2 | 运算放大器- |
| A3 | 运算放大器输出 |

## 数字引脚

UNO R4 WiFi共有14个数字引脚。尽管有些引脚有其他用途，如果有其他引脚可用，不应用于GPIO。  
导出ExcelJsonSQL

| 引脚 | 功能 | 注释 |
| --- | --- | --- |
| 0 | RX | 串行通信 |
| 1 | TX | 串行通信 |
| 2 | GPIO | 数字IO引脚 |
| 3 | PWM | 数字IO引脚，PWM |
| 4 | GPIO | 数字IO引脚 |
| 5 | PWM | 数字IO引脚，PWM |
| 6 | PWM | 数字IO引脚，PWM |
| 7 | GPIO | 数字IO引脚 |
| 8 | GPIO | 数字IO引脚 |
| 9 | PWM | 数字IO引脚，PWM |
| 10 | PWM | 数字IO引脚，PWM |
| 11 | PWM | 数字IO引脚，PWM |
| 12 | GPIO | 数字IO引脚 |
| 13 | GPIO | 数字IO引脚 |

所有数字引脚的参考电压是5V。

## PWM

PWM（脉冲宽度调制）功能允许数字引脚通过非常快速地开关来模拟模拟输出，从而让您做一些事情，比如调光连接到数字引脚的LED。  
UNO R4 WiFi支持在标有~的引脚上使用PWM。官方支持的引脚有：

| 引脚 | RA4M1 | 计时器 |
| --- | --- | --- |
| D3 | P105 | GTIOC1A |
| D5 | P107 | GTIOC0A |
| D6 | P111 | GTIOC3A |
| D9 | P303 | GTIOC7B |
| D10 | P103 | GTIOC2A |
| D11 | P411 | GTIOC6A |

您可以使用以下函数将它们作为模拟输出引脚：

```
analogWrite(pin, value);
```

默认情况下，分辨率是8位（0-255），您可以使用analogWriteResolution()来改变这一点，支持高达12位（0-4096）分辨率。

```
analogWriteResolution(resolution);
```

请注意，以下引脚能够进行PWM，但可能会干扰UNO R4 WiFi板的其他功能。编写库函数时，请不要使用这些，因为它们不是官方支持的PWM引脚。

| 引脚 | RA4M1 | 计时器 |
| --- | --- | --- |
| D0 | P301 | GTIOC4B |
| D1 | P302 | GTIOC4A |
| D2 | P104 | GTIOC1B |
| D4 | P106 | GTIOC0B |
| D7 | P112 | GTIOC3B |
| D8 | P304 | GTIOC7A |
| D12 | P410 | GTIOC6B |
| D13 | P102 | GTIOC2B |
| D18 / SDA | P101 | GTIOC5A |
| D19 / SCL | P100 | GTIOC5B |

## LED Matrix

UNO R4 WiFi 上的 LED 矩阵可以在您的程序中使用，用于显示静态图像、动画，甚至可以在其上玩游戏。Renesas 核心包括 Arduino\_LED\_Matrix 库，用于在矩阵上显示帧。

要深入了解 LED 矩阵，请查看 LED 矩阵指南。

Arduino\_LED\_Matrix matrix - 初始化 LED 矩阵。  
Arduino\_LED\_Matrix.load() - 将帧加载到帧缓冲区中。以下是一个基本示例：

```
// 创建两个帧的数组
const uint32_t frames[][4] = {
  {
    0x0,
    0x0,
    0xc00c0000,
    150
  },
  {
    0x0,
    0x1e01,
    0x201201e0,
    150
  }
}

// 将帧加载到矩阵缓冲区中
matrix.load(frames);
```

## DAC

UNO R4 WiFi 还包含一个最高 12 位分辨率的 DAC，它可以作为真正的模拟输出引脚，这意味着它的功能比 PWM 引脚更强大。

```
analogWrite(pin, value);
```

[![](https://arduino.me/storage/v1/object/public/image/437179c69f2da045d969395d1d612724.webp)](https://arduino.me/storage/v1/object/public/image/437179c69f2da045d969395d1d612724.webp)  
DAC 引脚  
此 DAC 引脚默认的写入分辨率为 8 位。这意味着写入到引脚的值应该在 0-255 之间。  
但是，如果需要，您可以将此写入分辨率更改为最高 12 位，在这种情况下，您写入到引脚的值应该在 0-4096 之间。

```
analogWriteResolution(12);
```

要了解更多关于 UNO R4 WiFi 的 DAC 功能，请查看 DAC 指南。

## RTC

实时时钟（RTC）用于测量时间，在任何跟踪时间的应用中都非常有用。  
UNO R4 WiFi 具有一个 VRTC 引脚，即使在电源被切断时也用于保持板载 RTC 的运行。为了使用它，请将 1.6 - 3.6 V 的电压应用于 VRTC 引脚。  
以下是一个最小示例，展示了如何从 RTC 获取日期和时间：

```
#include "RTC.h"

void setup() {
  Serial.begin(9600);

  RTC.begin();
  RTCTime mytime(30, Month::JUNE, 2023, 13, 37, 00, DayOfWeek::WEDNESDAY, SaveLight::SAVING_TIME_ACTIVE);

  RTC.setTime(mytime);
}

void loop() {
  RTCTime currenttime;

 // 从 RTC 获取当前时间
  RTC.getTime(currenttime);
  
  // 打印日期（日/月/年）
  Serial.print(currenttime.getDayOfMonth());
  Serial.print("/");
  Serial.print(Month2int(currenttime.getMonth()));
  Serial.print("/");
  Serial.print(currenttime.getYear());
  Serial.print(" - ");

  // 打印时间（时/分/秒）
  Serial.print(currenttime.getHour());
  Serial.print(":");
  Serial.print(currenttime.getMinutes());
  Serial.print(":");
  Serial.println(currenttime.getSeconds());

  delay(1000);
}
```

要了解更多关于 UNO R4 WiFi 的 RTC 功能，请查看 RTC 指南。

## EEPROM

EEPROM，也称为 'data' 内存，是一种在板子断电后仍能保留数据的内存类型。

```
EEPROM.write(address, val);
EEPROM.read(address);
```

它的写入周期有限，这意味着它最适合用于只读应用。确保永远不要在 void loop() 内使用 write()，因为您可能会用完芯片的所有写入周期。  
在 EEPROM 指南中阅读更多内容。  
要了解更多关于 UNO R4 WiFi 的 EEPROM 功能，请查看 EEPROM 指南。

## SPI

[![](https://arduino.me/storage/v1/object/public/image/67544b629632d11afa4b2b9ec011836c.webp)](https://arduino.me/storage/v1/object/public/image/67544b629632d11afa4b2b9ec011836c.webp)  
UNO R4 WiFi 特色的是一个串行外围接口（SPI）总线。总线（连接器）'SPI' 使用以下引脚：  
(COPI) - D11  
(CIPO) - D12  
(SCK) - D13  
(CS) - D10  
以下示例展示了如何使用 SPI：

```
#include <SPI.h>

const int CS = 10;

void setup() {
  pinMode(CS, OUTPUT);

  SPI.begin();

  digitalWrite(CS, LOW);

  SPI.transfer(0x00);
  
  digitalWrite(CS, HIGH);
}

void loop() {
}
```

## I2C

I2C 允许您使用两个引脚串联连接多个 I2C 兼容设备。控制器将通过 I2C 总线向 7 位地址发送信息，这意味着单条线上 I2C 设备的技术限制是 128 个。实际上，您在遇到其他限制之前，永远不会达到 128 个设备。  
UNO R4 WiFi 有一个 I2C 总线，它标有 SCL 和 SDA。它们与 A4（SDA）和 A5（SCL）共用，这是之前 UNO 的拥有者所熟悉的。PCB 上没有安装上拉电阻，但如果需要，有安装它们的足迹。  
UNO R4 WiFi 上用于 I2C 的引脚如下：

-   SDA - D14
-   SCL - D15

[![](https://arduino.me/storage/v1/object/public/image/3caab390668fe8431745c27e48ec486d.webp)](https://arduino.me/storage/v1/object/public/image/3caab390668fe8431745c27e48ec486d.webp)  
I2C 引脚  
要连接 I2C 设备，您需要在草图的顶部包含 Wire 库。

```
#include <Wire.h>
```

在 void setup() 内部，您需要初始化库，并初始化您想要使用的 I2C 端口。

```
Wire.begin(); //SDA & SDL
Wire1.begin(); //SDA1 & SDL1
Wire2.begin(); //SDA2 & SDL2
```

要向通过 I2C 连接的设备写入内容，我们可以使用以下命令：

```
Wire.beginTransmission(1); // 开始传输到设备 1
Wire.write(byte(0x00)); // 发送指令字节
Wire.write(val); // 发送一个值
Wire.endTransmission(); // 停止传输
```

## QWIIC连接器

[![](https://arduino.me/storage/v1/object/public/image/7e6dc9b5b959d70751f429fdc7266d65.webp)](https://arduino.me/storage/v1/object/public/image/7e6dc9b5b959d70751f429fdc7266d65.webp)  
UNO WiFi R4 上的 Qwiic 连接器  
UNO R4 WiFi 上的 Qwiic 连接器连接到第二个 I2C 总线（IIC0），它使用 Wire1 对象而不是 Wire 对象。请注意，Qwiic 连接器仅为 3.3 V。  
UNO R4 WiFi 特色的是一个 Qwiic/STEMMA 连接器，您可以使用它来连接模块，通常允许您通过单个连接器串联连接多个模块并控制它们。  
Qwiic 或 STEMMA 都是 SparkFun 和 Adafruit 分别开发的连接器类型的名称，它们将开发板和分线板模块的 I2C 引脚捆绑在一起。这意味着，如果您有一个开发板（例如 Arduino UNO R4 WiFi）和一个分线板模块，并且两者都有 Qwiic 或 STEMMA 连接器，您可以将它们连接在一起，几乎不需要任何接线，您就可以快速创建多功能项目。  
如果您的分线板上有不止一个这样的连接器，许多都有，您可以使用第二个来串联另一个 Qwiic 模块，为您的项目添加另一个交互节点。  
UNO R4 WiFi 有两个 I2C 总线，Qwiic 连接器连接到第二个。这意味着，如果您正在使用 Wire 库，您将需要使用 Wire1 对象而不是 Wire 对象，如下面的示例所示：

```
#include <Wire.h>

void setup(){
  Wire1.begin();
  Wire1.beginTransmission(1);   // 开始传输到设备 1
  Wire1.write(byte(0x00));      // 发送指令字节
  Wire1.write(val);             // 发送一个值
  Wire1.endTransmission();      // 停止传输
}
```

## USB串行 & UART

UNO R4 WiFi开发板具备2个独立的硬件串行端口。

-   一个端口通过USB-C®暴露，
-   另一个端口通过RX/TX引脚暴露。  
    这是UNO R3和UNO R4之间少数不同之处之一，因为UNO R3只有一个硬件串行端口，它同时连接到USB端口和板上的RX/TX引脚。

UNO R4 WiFi上用于UART的引脚如下：

| 引脚 | 功能 |
| --- | --- |
| D0 | RX（接收） |
| D1 | TX（发送） |

### 原生USB

使用标准Serial对象将串行数据发送到计算机。

```
Serial.begin(9600);
Serial.print("hello world");
```

要通过UART发送和接收数据，我们首先需要在`void setup()`内设置波特率。

### UART

UNO R4 WiFi上用于UART的引脚如下：  
导出ExcelJsonSQL

| 引脚 | 功能 |
| --- | --- |
| D0 | RX0 |
| D1 | TX0 |

要通过UART发送和接收数据，我们首先需要在`void setup()`内设置波特率。注意当使用UART（RX/TX引脚）时，我们使用Serial1对象。

```
Serial1.begin(9600);
复制
```

要读取传入的数据，我们可以使用一个while循环()来读取每个字符并将其添加到字符串中。

```
while(Serial1.available()){
    delay(2);
    char c = Serial1.read();
    incoming += c;
}
复制
```

要写入内容，我们可以使用以下命令：

```
Serial1.write("Hello world!");
复制
```

### Serial Event

`serialEvent()`方法在UNO板的旧版本上受支持，但在UNO R4板（或任何其他更新的Arduino板）上不受支持。  
然而，由于此方法仅用于检测串行数据并执行函数，您也可以使用Serial.available()来检测新数据何时可用：

```
if(Serial.available() > 0) {
  //code goes here
}
复制
```

### 计时器

在Ardunio API中有一个FspTimer类，它提供了在草图中使用计时器的所有必要功能。  
UNO R4 WiFi有两个计时器外设，一个异步通用计时器（AGT）和一个通用PWM计时器（GPT）。板上有两个AGT计时器，其中一个用于例如millis()和microseconds()等时间测量方法。  
板上有7个GPT计时器帮助执行PWM任务，例如通过测量信号活动的时间来计算占空比。可以通过使用前面提到的FspTimer库来使用这些保留的PWM计时器。使用此功能将明确请求一个PWM计时器：

```
FspTimer::force_use_of_pwm_reserved_timer();
复制
```

使用库的计时器功能时，您需要输入计时器类型。可以是AGT或GPT。可以在草图中这样声明：

```
uint8_t gpt_timer_type = GPT_TIMER;
uint8_t agt_timer_type = AGT_TIMER;
复制
```

### SerialUSB

UNO R4 WiFi具有一组扩展的Serial方法，可在您的草图中包含<HID.h>库时启用。

-   Serial.baud() - 返回当前使用的波特率（int）。
-   Serial.stopbits() - 返回通信中使用的停止位数（int）。
-   Serial.paritytype() - 返回通信中使用的奇偶校验类型（int）。
-   Serial.numbits() - 返回通信中使用的数据位数（int）。
-   Serial.dtr() - 返回数据终端就绪（DTR）信号的状态（bool），并且如果DTR信号被积极使用，则还将ignore\_dtr标志设置为true。
-   Serial.rts() - 返回请求发送（RTS）信号的状态（bool）。

<HID.h>库将Serial对象重映射为SerialUSB，从而启用这些附加功能。  
支持链接：

-   SerialUSB.h (Github)。
    

## USB HID

请注意，由于USB端口在UNO R4 WiFi上的实现方式，当使用HID时，开发板可能会显示为不同的USB端口。如果发生这种情况，只需双击重置按钮，然后再次选择您的开发板。  
该开发板可以充当HID（键盘/鼠标）并通过原生USB向计算机发送按键或坐标。

```
keyboard.press('W');
mouse.move(x,y);
复制
```

通过在IDE中的库管理器安装键盘和鼠标库，可以启用此支持。  
要了解更多有关UNO R4 WiFi的HID功能，请查看HID指南。

### Serial Remap

当在草图中包含<HID.h>库时，串行对象从Serial切换为SerialUSB以支持HID功能。这启用了更多方法，这里列出了。  
支持链接：

-   HID.h (Github)

## CAN模块

UNO R4 WiFi的RA4M1内置了符合CAN 2.0A/CAN 2.0B标准的CAN模块。  
引脚CANRX和CANTX可以连接到CAN收发器，例如MCP2551或TJA1050 IC。  
导出ExcelJsonSQL

| 引脚 | 功能 |
| --- | --- |
| D10 | CANRX |
| D13 | CANTX |

内置的Arduino\_CAN库用于与其他CAN设备通信。

```
//设置CAN位速率并在
//选择BR_125k,BR_250k,BR_500k,BR_1000k
CAN.begin(CanBitRate::BR_250k);
```

构造一个CAN消息并发送它：

```
uint8_t const msg_data[] = {0xCA,0xFE,0,0,0,0,0,0};
memcpy((void *)(msg_data + 4), &msg_cnt, sizeof(msg_cnt));
CanMsg msg(CAN_ID, sizeof(msg_data), msg_data);
CAN.write(msg);
```

读取传入的CAN消息。

```
CanMsg const msg = CAN.read(); //read
```

请注意，如果没有CAN收发器，就无法与其他CAN设备通信。  
要了解更多关于UNO R4 WiFi的CAN功能，请查看CAN指南。

## ESP32-S3-MINI-1-N8

默认情况下，UNO R4 WiFi上的ESP32-S3模块充当串行桥，处理与计算机的连接。它还处理主MCU，即Renesas RA4M1的重启，例如在接收新草图和重置时。  
在UNO R3上，ATMEGA16U2承担相同的功能。板载ESP32模块是一个更先进的SoC，为开发板添加了Wi-Fi®和Bluetooth®连接功能。  
ESP32还暴露了ESP32的数据线，以便您可以直接对ESP32进行编程。这些数据线通过板顶部的3x2排针暴露，或者通过板底部的焊盘暴露。

> 请注意，ESP32安装有默认固件，设置为与RA4M1芯片通信。任何对ESP32的直接编程都将覆盖该固件，直到恢复默认固件之前，芯片之间的通信可能会中断。

[![](https://arduino.me/storage/v1/object/public/image/2677b875ea01dfbb03652c6718a3cb45.webp)](https://arduino.me/storage/v1/object/public/image/2677b875ea01dfbb03652c6718a3cb45.webp)  
UNO R4 & UNO R3

### USB桥

默认情况下，ESP32充当计算机和RA4M1 MCU之间的串行桥。USB数据线通过开关路由，这些开关默认设置为通过ESP32模块进行通信。  
[![](https://arduino.me/storage/v1/object/public/image/3c4f40f98cb870333cd1044bce67bd08.webp)](https://arduino.me/storage/v1/object/public/image/3c4f40f98cb870333cd1044bce67bd08.webp)  
串行通信开关  
如果您愿意，可以更改此设置并直接访问RA4M1 MCU上的串行总线，无论是使用软件还是硬件。请参阅下面的说明：  
1\. 软件 - 通过将D21拉高至HIGH，您将关闭控制哪个MCU连接到USB的电路。当D21为HIGH时，RA4M1连接到USB串行端口，当D21为LOW时，ESP32连接，如默认配置。您可以通过在void setup()中包含以下代码来实现这一点

```
pinMode(21, OUTPUT);
digitalWrite(21, HIGH);
```

2\. 在UNO R4 WiFi的背面，您会找到标有"RA4M1 USB"的焊盘。如果您在这些焊盘之间创建短路，例如用焊锡在它们之间创建桥接，RA4M1将连接到USB串行端口，而不是ESP32。  
[![](https://arduino.me/storage/v1/object/public/image/f081e63703bf9bf82b8e59a06b2c24f5.webp)](https://arduino.me/storage/v1/object/public/image/f081e63703bf9bf82b8e59a06b2c24f5.webp)  
RA4M1 USB焊盘

### Wi-Fi®

UNO R4 WiFi上的ESP32用于赋予开发板Wi-Fi®功能。Wi-Fi®模块的比特率高达150 Mbps。ESP32模块内置了迹线天线，这意味着您不需要外部天线就可以使用开发板的连接功能。然而，这种迹线天线与Bluetooth®模块共享，这意味着您不能同时使用Bluetooth®和Wi-Fi®。  
要使用UNO R4 WiFi的Wi-Fi®功能，请使用内置于UNO R4 Core的WiFiS3库。  
要了解更多关于UNO R4 WiFi的Wi-Fi®功能，请尝试Network Examples。

### Bluetooth®

多亏了ESP32模块，UNO R4 WiFi具有Bluetooth® LE和Bluetooth® 5功能，速度高达2 Mbps。ESP32模块内置了迹线天线，这意味着您不需要外部天线就可以使用开发板的连接功能。然而，这种迹线天线与Bluetooth®模块共享，这意味着您不能同时使用Bluetooth®和Wi-Fi®。  
下面是一个扫描蓝牙设备的示例草图：

```
#include <ArduinoBLE.h>

void setup() {
  // ...省略其余代码...
}

void loop() {
  // ...省略其余代码...
}

void explorerPeripheral(BLEDevice peripheral) {
  // ...省略其余代码...
}

void exploreService(BLEService service) {
  // ...省略其余代码...
}

void exploreCharacteristic(BLECharacteristic characteristic) {
  // ...省略其余代码...
}

void exploreDescriptor(BLEDescriptor descriptor) {
  // ...省略其余代码...
}

void printData(const unsigned char data[], int length) {
  // ...省略其余代码...
}
```

如果您想了解更多关于Bluetooth LE的信息，请查看我们的文章。

### 编程ESP32（高级）

ESP32模块和Renesas RA4M1芯片是一个复杂的USB-串行系统的一部分，这个系统具有很高的灵活性和适应性，能够在保持编程主MCU和ESP32的能力的同时允许HID功能。默认情况下，ESP32主要用作使用Wi-Fi®和Bluetooth®的无线模块。  
覆盖ESP32的固件会中断两个MCU之间的通信，但使它们能够独立行动。如果您希望将开发板恢复到初始状态，您可以按照我们帮助中心文章中的espflash步骤操作。

> 注意：要重新编程ESP32模块，您需要在重置开发板时将ESP\_Download引脚短接至GND。这将使ESP32模块进入引导加载程序状态，在该状态下您可以与之建立连接并重新编程模块。

要重新编程ESP32开发板，您可以在ESP32模块旁边找到UART焊盘，其布局如下图所示：  
[![](https://arduino.me/storage/v1/object/public/image/21cf7bdd8f9d9323153022d39d08a5c2.webp)](https://arduino.me/storage/v1/object/public/image/21cf7bdd8f9d9323153022d39d08a5c2.webp)  
暴露的ESP32数据焊盘  
或者您可以直接使用ESP32排针上暴露的引脚，如下所示：  
[![](https://arduino.me/storage/v1/object/public/image/01467c9f8030270bbabf20fcae6af6e9.webp)](https://arduino.me/storage/v1/object/public/image/01467c9f8030270bbabf20fcae6af6e9.webp)  
ESP32数据引脚排针