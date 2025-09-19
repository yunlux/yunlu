---
{"dg-publish":true,"permalink":"/09/arduino-nano-button-led-arduino-nano-tutorial/","created":"2024-09-16T00:59:18.083+08:00","updated":"2024-09-23T13:33:06.453+08:00"}
---

This tutorial instructs you how to use the Arduino Nano and button to control the LED. We will learn two different applications:

**Application 1 -** The LED state is synchronized with the button state. In detail:

-   Arduino Nano turns on the LED when the button is being pressed.
    
-   Arduino Nano turns off the LED when the button is NOT being pressed.
    

**Application 2 -** The LED state is toggled each time the button is pressed. More specifically:

-   If Arduino Nano detects that the button has been pressed (changing from a HIGH state to a LOW state), it will turn ON the LED if it's currently OFF, or turn OFF the LED if it's currently ON.
    
-   Releasing the button does not affect to the LED state.
    

In the **Application 2**, We need to debounce the button to make sure it works properly. We'll figure out why it's important by comparing how the LED behaves when we use the Arduino code with and without debouncing the button.

<table><tbody><tr><td>1</td><td>×</td><td><a href="https://amzn.to/3jZdvxa" target="_blank">Arduino Nano</a></td><td><i></i></td></tr><tr><td>1</td><td>×</td><td><a href="https://amzn.to/3rCstmt" target="_blank">USB A to Mini-B USB cable</a></td><td><i></i></td></tr><tr><td>1</td><td>×</td><td><a href="https://amzn.to/3KJh5fl" target="_blank">Breadboard-mount Button with Cap</a></td><td><i></i></td></tr><tr><td>1</td><td>×</td><td><a href="https://amzn.to/3YCqHQ9" target="_blank">Breadboard-mount Button Kit</a></td><td><i></i></td></tr><tr><td>1</td><td>×</td><td><a href="https://amzn.to/4ag4oTL" target="_blank">Panel-mount Push Button</a></td><td><i></i></td></tr><tr><td>1</td><td>×</td><td><a href="https://amzn.to/43kslGm" target="_blank">LED</a></td><td><i></i></td></tr><tr><td>1</td><td>×</td><td><a href="https://amzn.to/3Y9JrmK" target="_blank">220 ohm resistor</a></td><td><i></i></td></tr><tr><td>1</td><td>×</td><td><a href="https://amzn.to/46Y5TnT" target="_blank">Breadboard</a></td><td><i></i></td></tr><tr><td>1</td><td>×</td><td><a href="https://amzn.to/3RuHEag" target="_blank">Jumper Wires</a></td><td><i></i></td></tr><tr><td>1</td><td>×</td><td><a href="https://amzn.to/3NeaCbW" target="_blank">(Optional) 9V Power Adapter for Arduino Nano</a></td><td><i></i></td></tr><tr><td>1</td><td>×</td><td><a href="https://amzn.to/49ditAq" target="_blank">(Recommended) Screw Terminal Expansion Board for Arduino Nano</a></td><td><i></i></td></tr></tbody></table>

Or you can buy the following sensor kits:

Disclosure: Some of the links provided in this section are Amazon

affiliate

links. We may receive a commission for any purchases made through these links at no additional cost to you.  
Additionally, some of these links are for products from our own brand, **DIYables**.

If you are unfamiliar with LED and button (including pinout, operation, and programming), the following tutorials can help:

![The wiring diagram between Arduino Nano and Button LED](https://newbiely.com/images/tutorial/arduino-nano-button-led-wiring-diagram.jpg)

This image is created using [Fritzing](http://fritzing.org/). Click to enlarge image

**

const int BUTTON\_PIN = 2; const int LED\_PIN = 5; int button\_state = 0; void setup() { pinMode(LED\_PIN, OUTPUT); pinMode(BUTTON\_PIN, INPUT\_PULLUP); } void loop() { button\_state = digitalRead(BUTTON\_PIN); if(button\_state == LOW) digitalWrite(LED\_PIN, HIGH); else digitalWrite(LED\_PIN, LOW); }

-   Connect an Arduino Nano to your computer with a USB cable.
    
-   Launch the Arduino IDE, and select the correct board and port.
    
-   Copy the code and open it in the Arduino IDE.
    
-   Click the Upload button on the Arduino IDE to compile and upload the code to the Arduino Nano.
    

![Arduino IDE Upload Code](https://newbiely.com/images/tutorial/how-to-upload-code-to-arduino-nano.jpg)

-   Press the button and hold it for a few seconds.
    
-   Check out the
    
    alteration
    
    in the LED's condition.
    

You will see that the LED state is in sync with the button state.

Check out the line-by-line explanation contained in the comments of the source code!

**

const int BUTTON\_PIN = 2; const int LED\_PIN = 5; int led\_state = LOW; int prev\_button\_state; int button\_state; void setup() { Serial.begin(9600); pinMode(BUTTON\_PIN, INPUT\_PULLUP); pinMode(LED\_PIN, OUTPUT); button\_state = digitalRead(BUTTON\_PIN); } void loop() { prev\_button\_state = button\_state; button\_state = digitalRead(BUTTON\_PIN); if(prev\_button\_state == HIGH && button\_state == LOW) { Serial.println("The button is pressed"); led\_state = !led\_state; digitalWrite(LED\_PIN, led\_state); } }

You can locate the explanation in the comment lines of the Arduino Nano code above.

In the code, the expression led\_state = !led\_state is equal to the following code:

**

if(led\_state == LOW) led\_state = HIGH; else led\_state = LOW;

-   Copy the code and open it in the Arduino IDE.
    
-   Upload the code to the Arduino Nano.
    
-   Press release and button several times.
    
-   Check out the change in the LED's state.
    

You may observe that the LED state is toggled every time the button is pressed. However, this behavior may not always be consistent. At times, the LED state may be rapidly toggled multiple times within a single button press, or it may not toggle at all(toggling twice in quick succession which can be difficult to see with the naked eye).

⇒ To solve this problem, we need to [debounce for the button](https://newbiely.com/tutorials/arduino-nano/arduino-nano-button-debounce).

Debouncing a button can be challenging for beginners. Fortunately, [the ezButton library](https://arduinogetstarted.com/tutorials/arduino-button-library) makes it easy.

Why is debouncing necessary? See the [Arduino Nano - Button Debounce tutorial](https://newbiely.com/tutorials/arduino-nano/arduino-nano-button-debounce) for more information.

**

#include <ezButton.h> const int BUTTON\_PIN = 2; const int LED\_PIN = 5; ezButton button(BUTTON\_PIN); int led\_state = LOW; void setup() { Serial.begin(9600); pinMode(LED\_PIN, OUTPUT); button.setDebounceTime(50); } void loop() { button.loop(); if(button.isPressed()) { Serial.println("The button is pressed"); led\_state = !led\_state; digitalWrite(LED\_PIN, led\_state); } }

-   Install the ezButton library. Refer to [How To](https://arduinogetstarted.com/tutorials/arduino-button-library#content_how_to_install_library) for instructions.
    
-   Copy the code and open it with Arduino IDE.
    
-   Click the Upload button on Arduino IDE to upload the code to the Arduino Nano.
    
-   Press and release the button multiple times.
    
-   Check out the LED's state change.
    

You will see that the LED state is toggled exactly once each time the button is pressed.

***※ OUR MESSAGES***

-   Please feel free to share the link of this tutorial. However, Please do not use our content on any other websites. We invested a lot of effort and time to create the content, please respect our work!