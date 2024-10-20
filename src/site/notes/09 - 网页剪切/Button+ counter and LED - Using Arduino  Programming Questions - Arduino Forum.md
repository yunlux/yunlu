---
{"dg-publish":true,"permalink":"/09 - 网页剪切/Button+ counter and LED - Using Arduino  Programming Questions - Arduino Forum/"}
---

Hi,  
I want to make my LED turn on as many times as I have pressed a button. For example I have pressed the button 4 times and then after some time the LED lights up 4 times. I have managed to make a counter for the presses but after that I got stuck. I don't know what should I do next ![:confused:](https://emoji.discourse-cdn.com/twitter/confused.png?v=12 ":confused:")

P.S. That's my first time using the forum ![:slight_smile:](https://emoji.discourse-cdn.com/twitter/slight_smile.png?v=12 ":slight_smile:")

Also, sorry for not adding the code ![:slight_smile:](https://emoji.discourse-cdn.com/twitter/slight_smile.png?v=12 ":slight_smile:")  
I have messed it up in the end but..I am still trying ![:slight_smile:](https://emoji.discourse-cdn.com/twitter/slight_smile.png?v=12 ":slight_smile:")

```
 int btnPin = 2;
  int ledPin = 6;
  int counter = 0;
  int buttonState = 0;
  int lastBtnState= 0;
  
  void setup() {
  
  pinMode(ledPin, OUTPUT);
  pinMode(btnPin, INPUT);
  Serial.begin(9600);
}
void loop() {
  buttonState = digitalRead(btnPin);
  if (buttonState != lastBtnState) {
  
    if (buttonState == HIGH) {
      
      counter++;
      Serial.println("on");
      Serial.print("number of button pushes: ");
      Serial.println(counter);
    } else {
      // if the current state is LOW then the button went from on to off:
      Serial.println("off");
    }
    // Delay a little bit to avoid bouncing
    delay(50);
  }
 
  lastBtnState = buttonState;

   for(int i= 0; i < counter; i++)
   {
    digitalWrite(ledPin, HIGH);
    delay(500);
    digitalWrite(ledPin, LOW);
  }
}
```

Welcome to the Forum. Please read these two posts:  
[  
General Guidance and How to use the Forum 1](https://forum.arduino.cc/index.php?topic=652233.0) and  
[Read this before posting a programming question ...](https://forum.arduino.cc/index.php?topic=97455.0)  
You may also find useful information that would answer your question here:  
[Useful links - check here for reference posts / tutorials 2](https://forum.arduino.cc/index.php?topic=384198.0)

It is important to provide as much of the information that is needed to solve your problem as you can, in your first posts. The forum link above has guidelines for posting in a standard way that makes it easiest for people to provide you with useful answers. Making an effort to do this will greatly increase the number and quality of helpful responses that you get.

We are not mind readers, so we can't guess what your problem is. Please post your code using code tags. The code tags make the code look

```
like this
```

when posting source code files. It makes it easier to read, and can be copied with a single mouse click. Also, if you don't do it, some of the character sequences in the code can be misinterpred by the forum code as italics or funny emoticons. The "Code: \[Select\]" feature allows someone to select the entire sketch so it can be easily copied and pasted into the IDE for testing or review.

I'm not 100% clear what you mean: do you mean that it counts presses, then waits some time to make sure you have finished clicking (eg it's on 1... are you done?... or is #2 still coming? it's on 4... are you done?... or is #5 still coming?... ) then blinks that number of times?

If so then you need to capture millis() when the button becomes pressed, as well as incrementing the counter. Then if there's no new press before a certain time is up, stop looking at the button and go off to another state and do "n" blinks. If there is a press before the time is up, capture the new time, etc.

I am so incredibly bored: here's a sketch based on my understanding in #2.

Button is wired from pin 8 to ground, the led on pin 13 blinks all the time like a pulse, and the led that blinks "n" times is on pin 7.

The timeout is currently 5 seconds, set that in buttonPressTimeout.

Run the code with the serial monitor open to see the messages.

SPOILER ALERT: fully working code below

```
// https://forum.arduino.cc/index.php?topic=678413
// 18 april 2020

/*
  op prodaamjanti asks:
  I want to make my LED turn on as many times as I have
  pressed a button. For example I have pressed the button 4
  times and then after some time the LED lights up 4 times
*/

//states
enum {ST_waiting, ST_counting, ST_blinking} currentState = ST_waiting;
// ala https://www.gammon.com.au/statemachine

//pulse
unsigned long previousPulse;
bool pulseState;
int pulseInterval = 500;

const byte button = 8;
byte count = 0;
unsigned long lastPress = 0;
int buttonPressTimeout = 5000;

bool buttonState;
bool lastButtonState;

//the blinker
unsigned long lastBlink;
const int blinkInterval = 250;
byte blinksComplete;
bool blinkState = LOW;
const byte theLed = 7;

void setup()
{
  // initialize serial communication:
  Serial.begin(9600);
  Serial.println("setup() ... ");
  Serial.println("*** forum 678413 ***");
  Serial.print("Compiler: ");
  Serial.print(__VERSION__);
  Serial.print(", Arduino IDE: ");
  Serial.println(ARDUINO);
  Serial.print("Created: ");
  Serial.print(__TIME__);
  Serial.print(", ");
  Serial.println(__DATE__);
  Serial.println(__FILE__);

  pinMode(LED_BUILTIN, OUTPUT);
  digitalWrite(LED_BUILTIN, pulseState);
  pinMode(theLed, OUTPUT);
  pinMode(button, INPUT_PULLUP);
  //initialize button states
  buttonState = digitalRead(button);
  lastButtonState = buttonState;

  Serial.println("setup() done");
  Serial.println(" ");
  Serial.print("Count is "); Serial.println(count);
  Serial.println("Press the button to start counting");
}//setup

void loop()
{
  doPulse();
  manageStates();
} //loop

void manageStates()
{
  switch (currentState) //ST_waiting, ST_counting, ST_blinking
  {
    case ST_waiting:
      // do any required stuff here

      if (checkButtonForNewPress()) //it returns a bool
      {
        currentState = ST_counting;
        count = 1;
        lastPress = millis();
        Serial.print(", entering counting state with count of ");
        Serial.println(count);
        blinksComplete = 0;
      }

      break;

    case ST_counting:
      if (checkButtonForNewPress())
      {
        count++;
        Serial.print(", count is ");
        Serial.println(count);
        lastPress = millis();
      }

      if (millis() - lastPress >= (unsigned long) buttonPressTimeout)
      {
        currentState = ST_blinking;
        Serial.print("Time out, entering blinking state with count of ");
        Serial.println(count);
      }
      break;

    case ST_blinking:
      //blink "count" times
      if (millis() - lastBlink >= blinkInterval && blinksComplete < count)
      {
        lastBlink = millis();
        blinkState = !blinkState;
        digitalWrite(theLed, blinkState);
        if (blinkState == LOW)
        {
          blinksComplete++;
          Serial.print("Blink #"); Serial.println(blinksComplete);
        }
        break;
      }

      if (blinksComplete == count)
      {
        Serial.println("Blinking is complete, returning to waiting state ");
        count = 0;
        Serial.print("Count is reset to "); Serial.println(count);
        Serial.println("Press the button to start counting");
        currentState = ST_waiting;
      }

  }//switch
}//manageStates

bool checkButtonForNewPress()
{
  bool result = false;
  // read the button:
  buttonState = digitalRead(button);

  // compare the buttonState to its previous state
  if (buttonState != lastButtonState) // != means not equal, so it changed one way or the other
  {
    if (buttonState == LOW) //... and if it's now low, that's a press
    {
      Serial.print("New press");
      result = true;
    }// change to low

    // Delay a little bit to avoid bouncing
    delay(50);
  }//change
  // save the current state as the last state, for next time through the loop
  lastButtonState = buttonState;
  return result;
}

void doPulse()
{
  if (millis() - previousPulse >= (unsigned long)pulseInterval)
  {
    previousPulse = millis();
    pulseState = !pulseState;
    digitalWrite(LED_BUILTIN, pulseState);
  }
}//do pulse
```

I have tried the code from #3 and it is totally working ![:slight_smile:](https://emoji.discourse-cdn.com/twitter/slight_smile.png?v=12 ":slight_smile:")

As I thought it's too hard for me LOL

Thanks for the help and the support ![:slight_smile:](https://emoji.discourse-cdn.com/twitter/slight_smile.png?v=12 ":slight_smile:")

That's a pretty lengthy sketch for such a simple task.

Here's my submission:

```
[color=#5e6d03]#include[/color] [color=#434f54]<[/color][b][color=#d35400]Arduino_Helpers[/color][/b][color=#434f54].[/color][color=#000000]h[/color][color=#434f54]>[/color]
[color=#5e6d03]#include[/color] [color=#434f54]<[/color][b][color=#d35400]AH[/color][/b][color=#434f54]/[/color][color=#000000]Hardware[/color][color=#434f54]/[/color][b][color=#d35400]Button[/color][/b][color=#434f54].[/color][color=#000000]hpp[/color][color=#434f54]>[/color]
[color=#5e6d03]#include[/color] [color=#434f54]<[/color][b][color=#d35400]AH[/color][/b][color=#434f54]/[/color][color=#000000]Timing[/color][color=#434f54]/[/color][color=#000000]MillisMicrosTimer[/color][color=#434f54].[/color][color=#000000]hpp[/color][color=#434f54]>[/color]

[color=#434f54]// Push button on pin 2 (other pin to ground)[/color]
[b][color=#d35400]Button[/color][/b] [color=#d35400]button[/color] [color=#434f54]=[/color] [color=#000000]2[/color][color=#000000];[/color]
[color=#434f54]// Built-in LED is used for blinking[/color]
[color=#00979c]const[/color] [color=#00979c]uint8_t[/color] [color=#000000]ledPin[/color] [color=#434f54]=[/color] [color=#00979c]LED_BUILTIN[/color][color=#000000];[/color]
[color=#434f54]// How long to wait after the last time the[/color]
[color=#434f54]// button was pressed before starting to blink[/color]
[color=#00979c]const[/color] [color=#00979c]unsigned[/color] [color=#00979c]long[/color] [color=#000000]blinkStartDelay[/color] [color=#434f54]=[/color] [color=#000000]1000[/color][color=#000000];[/color]
[color=#434f54]// Timer for half the blink period[/color]
[b][color=#d35400]Timer[/color][/b][color=#434f54]<[/color][color=#d35400]millis[/color][color=#434f54]>[/color] [color=#000000]blinkTimer[/color] [color=#434f54]=[/color] [color=#000000]500[/color][color=#000000];[/color]

[color=#00979c]void[/color] [color=#5e6d03]setup[/color][color=#000000]([/color][color=#000000])[/color] [color=#000000]{[/color]
  [color=#d35400]button[/color][color=#434f54].[/color][color=#d35400]begin[/color][color=#000000]([/color][color=#000000])[/color][color=#000000];[/color] [color=#434f54]// enables internal pull-up resistor[/color]
  [color=#d35400]pinMode[/color][color=#000000]([/color][color=#000000]ledPin[/color][color=#434f54],[/color] [color=#00979c]OUTPUT[/color][color=#000000])[/color][color=#000000];[/color]
[color=#000000]}[/color]

[color=#00979c]void[/color] [color=#5e6d03]loop[/color][color=#000000]([/color][color=#000000])[/color] [color=#000000]{[/color]
  [color=#00979c]static[/color] [color=#00979c]bool[/color] [color=#000000]blinking[/color] [color=#434f54]=[/color] [color=#00979c]false[/color][color=#000000];[/color] [color=#434f54]// Are we currently blinking?[/color]
  [color=#00979c]static[/color] [color=#00979c]uint8_t[/color] [color=#000000]counter[/color] [color=#434f54]=[/color] [color=#000000]0[/color][color=#000000];[/color]   [color=#434f54]// How many blinks are left?[/color]

  [color=#434f54]// Add one to the counter if the button is pressed[/color]
  [color=#5e6d03]if[/color] [color=#000000]([/color][color=#d35400]button[/color][color=#434f54].[/color][color=#d35400]update[/color][color=#000000]([/color][color=#000000])[/color] [color=#434f54]==[/color] [b][color=#d35400]Button[/color][/b][color=#434f54]:[/color][color=#434f54]:[/color][color=#00979c]Falling[/color][color=#000000])[/color]
    [color=#434f54]++[/color][color=#000000]counter[/color][color=#000000];[/color]

  [color=#434f54]// If we're not already blinking, and the button has been [/color]
  [color=#434f54]// released long enough, reset timer and start blinking[/color]
  [color=#5e6d03]if[/color] [color=#000000]([/color][color=#434f54]![/color][color=#000000]blinking[/color]
   [color=#434f54]&&[/color] [color=#000000]counter[/color] [color=#434f54]>[/color] [color=#000000]0[/color]
   [color=#434f54]&&[/color] [color=#d35400]button[/color][color=#434f54].[/color][color=#d35400]getState[/color][color=#000000]([/color][color=#000000])[/color] [color=#434f54]==[/color] [b][color=#d35400]Button[/color][/b][color=#434f54]:[/color][color=#434f54]:[/color][color=#00979c]Released[/color]
   [color=#434f54]&&[/color] [color=#d35400]button[/color][color=#434f54].[/color][color=#d35400]stableTime[/color][color=#000000]([/color][color=#000000])[/color] [color=#434f54]>=[/color] [color=#000000]blinkStartDelay[/color]
  [color=#000000])[/color] [color=#000000]{[/color]
    [color=#000000]blinking[/color] [color=#434f54]=[/color] [color=#00979c]true[/color][color=#000000];[/color]
    [color=#000000]blinkTimer[/color][color=#434f54].[/color][color=#d35400]begin[/color][color=#000000]([/color][color=#000000])[/color][color=#000000];[/color] 
  [color=#000000]}[/color]

  [color=#434f54]// If we're blinking and the timer indicates another 500 ms[/color]
  [color=#434f54]// have passed, toggle the state of the LED[/color]
  [color=#5e6d03]if[/color] [color=#000000]([/color][color=#000000]blinking[/color] [color=#434f54]&&[/color] [color=#000000]blinkTimer[/color][color=#000000])[/color] [color=#000000]{[/color]
     [color=#00979c]bool[/color] [color=#000000]ledState[/color] [color=#434f54]=[/color] [color=#d35400]digitalRead[/color][color=#000000]([/color][color=#000000]ledPin[/color][color=#000000])[/color][color=#000000];[/color]
     [color=#d35400]digitalWrite[/color][color=#000000]([/color][color=#000000]ledPin[/color][color=#434f54],[/color] [color=#434f54]![/color][color=#000000]ledState[/color][color=#000000])[/color][color=#000000];[/color]
     [color=#5e6d03]if[/color] [color=#000000]([/color][color=#000000]ledState[/color][color=#000000])[/color] [color=#000000]{[/color]           [color=#434f54]// if the led is now off[/color]
       [color=#434f54]--[/color][color=#000000]counter[/color][color=#000000];[/color]              [color=#434f54]// decrement the counter and[/color]
       [color=#000000]blinking[/color] [color=#434f54]=[/color] [color=#000000]counter[/color] [color=#434f54]>[/color] [color=#000000]0[/color][color=#000000];[/color] [color=#434f54]// stop blinking if it's zero[/color]
     [color=#000000]}[/color]
  [color=#000000]}[/color]
[color=#000000]}[/color]
```

It makes use of the [Arduino Helpers 2](https://github.com/tttapa/Arduino-Helpers) library for the right level of abstraction.

Pieter

It looks a little bit more complicated ![:slight_smile:](https://emoji.discourse-cdn.com/twitter/slight_smile.png?v=12 ":slight_smile:")