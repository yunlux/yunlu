---
{"dg-publish":true,"permalink":"/09/harm-and-fab-academy/","created":"2024-09-15T19:47:26.610+08:00","updated":"2024-09-15T19:47:26.611+08:00"}
---

During the months I have been expirimenting with these inks & Dyes.

-   [Theory about Thermochromic paint](http://fabacademy.org/2020/labs/waag/students/harm-vanvugt/posts/2020/01/01/thermoInks.html#theory-about-thermochromic-paint)
-   [Experiments using Leuco dye](http://fabacademy.org/2020/labs/waag/students/harm-vanvugt/posts/2020/01/01/thermoInks.html#experiments-using-leuco-dye)
    -   [Heatpath & 31°C Aliexpress Dye (25 march)](http://fabacademy.org/2020/labs/waag/students/harm-vanvugt/posts/2020/01/01/thermoInks.html#heatpath--31c-aliexpress-dye-25-march)
    -   [31°C Aliexpress Dye (17 march)](http://fabacademy.org/2020/labs/waag/students/harm-vanvugt/posts/2020/01/01/thermoInks.html#31c-aliexpress-dye-17-march)
    -   [47°C SFXC screen Ink (11 march)](http://fabacademy.org/2020/labs/waag/students/harm-vanvugt/posts/2020/01/01/thermoInks.html#47c-sfxc-screen-ink-11-march)
    -   [42°C nailpolisch (1 febr) and nichrome wire](http://fabacademy.org/2020/labs/waag/students/harm-vanvugt/posts/2020/01/01/thermoInks.html#42c-nailpolisch-1-febr-and-nichrome-wire)
    -   [30°C Dye from Hackerstore (28 febr)](http://fabacademy.org/2020/labs/waag/students/harm-vanvugt/posts/2020/01/01/thermoInks.html#30c-dye-from-hackerstore-28-febr)
-   [How to heat Leuco Dye?](http://fabacademy.org/2020/labs/waag/students/harm-vanvugt/posts/2020/01/01/thermoInks.html#how-to-heat-leuco-dye)
-   [Heating the paint](http://fabacademy.org/2020/labs/waag/students/harm-vanvugt/posts/2020/01/01/thermoInks.html#heating-the-paint)

---

## Theory about Thermochromic paint

From [how Thermochromic paint works](https://electronics.howstuffworks.com/gadgets/other-gadgets/thermochromic-ink5.htm)

Two types:

1.  Thermochromic liquid crystals (TLCs)
    -   Change from black to every color
    -   Precise display of temperature
    -   Suffer from UV light, water and chemicals, so Hard to Process
    -   Applications: thermometer

Example of TLC

I can only [buy an TLC](https://www.sfxc.co.uk/products/sprayable-liquid-crystal-inks) with a temperature range from 24°C to 29°C. In the summer the kitchen can be 24°C.

1.  Leuco dyes
    -   Will show if something is HOT or COLD
    -   Change from a color to transparent
    -   Relatively easy to apply and keep stable
    -   Applications: coffee cups, beer cans,

I can find [several colors from SFXC with different temperatures](https://www.sfxc.co.uk/collections/thermochromic-pigment)

## Experiments using Leuco dye

### Heatpath & 31°C Aliexpress Dye (25 march)

### 31°C Aliexpress Dye (17 march)

Red. I mixed it with epoxi and it responds really well to [Thermochromic pigment - HALI](https://trade.aliexpress.com/order_detail.htm?spm=a2g0s.9042311.0.0.1ece4c4dbek1r7&orderId=3003039962952225)

Conclusion: this 31°C mixed with epoxi is working very well!

### 47°C SFXC screen Ink (11 march)

I bought 47°C thermocromatic paint, Black and Red at [sfxc.co.uk](https://www.sfxc.co.uk/collections/thermochromic-paint/products/thermochromic-screen-printing-ink-black-47-c) ![](http://fabacademy.org/2020/labs/waag/students/harm-vanvugt/assets/images/finalAssignment/thermotest47C.jpg) Conclusion: this is working well. But the temperature of 47C is really high

### 42°C nailpolisch (1 febr) and nichrome wire

I borrowed nailpolisch 42°C, I used Nichrome and a power supply and a NickCrome wire to heat it. ![](http://fabacademy.org/2020/labs/waag/students/harm-vanvugt/assets/images/finalAssignment/thermotest4.jpg) ![](http://fabacademy.org/2020/labs/waag/students/harm-vanvugt/assets/images/finalAssignment/thermotest5.jpg)

### 30°C Dye from Hackerstore (28 febr)

I did a test with Thermochromic Pigment. Borrowed from the [Loes Bogers](https://class.textile-academy.org/2020/loes.bogers/assignments/week10/#thermochromic-pigment-heating-pad) (textile Academy). It is 30°C green dye. I mixed a pinch of dye with wood glue.

| In the fridge | Hand warmed | left in the room for 1 hour |
| --- | --- | --- |
| ![](http://fabacademy.org/2020/labs/waag/students/harm-vanvugt/assets/images/finalAssignment/thermotest1.jpg) | ![](http://fabacademy.org/2020/labs/waag/students/harm-vanvugt/assets/images/finalAssignment/thermotest2.jpg) | ![](http://fabacademy.org/2020/labs/waag/students/harm-vanvugt/assets/images/finalAssignment/thermotest3.jpg) |

---

## How to heat Leuco Dye?

1.  Copper PCB
2.  Nicrome wire
3.  Carbon fibre

I tried carbon fibre and Nicrome wire, see below.

But I did not try copper, I don’t have the space to create a really long Copper trace. And I have seen a lot of examples burning the PCB. This is explained in this post: [https://www.quora.com/Why-cant-we-use-copper-material-in-the-place-of-nichrome-in-heating-coil](https://www.quora.com/Why-cant-we-use-copper-material-in-the-place-of-nichrome-in-heating-coil)

```
The high conductivity of copper could be overcome by using a very long length of wire of a very small cross sectional area. Also being a near pure element in use with a melting point of just over 1000 degrees C it will have a stable micro structure during use. That is providing there is a good thermaly conducive path to a heated bed and so its not allowed to glow “red hot” at any point. The problem of corrosion could also be eliminated provided the copper is removed from oxygen, such as when covered by fire cement or polyimide tape.

So why go to all this trouble when nichrome wire is so cheap and widely available so we use nichrome in heating coil.

Nichrome being 100 times more resisistive than copper produces good amount of heat when current passed through it and it overcomes the usage of copper having low resistivity and high conductivity in heating coil.
```

Since the esp/arduino boards have only a few outputs and I Want 30 hours of forecast, I have to multiply the numer of outputs.

-   Multiplexer. A multiplexer IC [Datasheet CD4052](https://www.alldatasheet.com/datasheet-pdf/pdf/8180/NSC/CD4052BM.html)
-   Create a multiplexer board
-   The [MC74HC4067A](https://www.onsemi.com/pub/Collateral/MC74HC4067A-D.PDF) runs on 2 to 6 volt and offers a 4 input to 16 chanel output ![](http://fabacademy.org/2020/labs/waag/students/harm-vanvugt/assets/images/finalAssignment/thermotest47C.jpg)

## Heating the paint

1.  Wire: [Nichrome](https://en.wikipedia.org/wiki/Nichrome) 27 march I received the Wire via Aliexpress. This are the specs from the site of the seller: ![](http://fabacademy.org/2020/labs/waag/students/harm-vanvugt/assets/images/finalAssignment/NiChromeWireTable.jpg)

How to calculate the temperature in a nichrome wire? [https://www.youtube.com/watch?v=QNS0LrlRHbs](https://www.youtube.com/watch?v=QNS0LrlRHbs)

1.  Heat path made from Carbon fibers

[The heat paths I’ve ordered](https://www.aliexpress.com/snapshot/0.html?spm=a2g0s.9042647.0.0.47c44c4dlyFlEz&orderId=3003222997732225&productId=32959270697) ![](http://fabacademy.org/2020/labs/waag/students/harm-vanvugt/assets/images/finalAssignment/heatpaths.jpg)

![](http://fabacademy.org/2020/labs/waag/students/harm-vanvugt/assets/images/finalAssignment/heatpaths2.jpg) ![](http://fabacademy.org/2020/labs/waag/students/harm-vanvugt/assets/images/finalAssignment/heatpaths3.jpg) ![](http://fabacademy.org/2020/labs/waag/students/harm-vanvugt/assets/images/finalAssignment/heatpaths3.jpg)

I tried to make a heatpath with multiple angels, to display 8 different times. ![](http://fabacademy.org/2020/labs/waag/students/harm-vanvugt/assets/images/finalAssignment/carbonClock.jpg)

But keeping the wires attached to the heatpath was a struggle. The heat was not evenly divided on the path. And the center became very hot. ![](http://fabacademy.org/2020/labs/waag/students/harm-vanvugt/assets/images/finalAssignment/heatCarbon1.jpg)