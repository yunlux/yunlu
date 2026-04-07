---
{"dg-publish":true,"permalink":"/09 - 网页剪切/Arduino + 按键开关实现简单的计数器 – Arduino 实验室/","created":"2024-09-16T00:53:12.010+08:00","updated":"2024-09-16T00:54:51.660+08:00","dg-note-properties":{"page-title":"Arduino + 按键开关实现简单的计数器 – Arduino 实验室","url":"https://arduino.nxez.com/2018/07/07/arduino-pushbutton-switch-for-simple-counter.html?variant=zh-cn","date":"2024-09-16 00:54:51"}}
---

本实验用以下材料，简单实现一个按键次数的计数器，统计按键被按下的次数，现实在串口输出栏。  
所用材料：  
Arduino UNO电路板（1块）  
面包板（1块）  
10k电阻（1个）  
按键开关（1个）  
面包线（3根）

按照下图方式将元件和Arduino连接起来。  
![](https://arduino.nxez.com/wp-content/uploads/2018/07/20180707103738992-0.jpg)

在 Arduino IDE 中新建一个代码文件，输入下面的代码。代码的功能看注释就好了。

<table><tbody><tr><td><p>1</p><p>2</p><p>3</p><p>4</p><p>5</p><p>6</p><p>7</p><p>8</p><p>9</p><p>10</p><p>11</p><p>12</p><p>13</p><p>14</p><p>15</p><p>16</p><p>17</p><p>18</p><p>19</p><p>20</p><p>21</p><p>22</p><p>23</p><p>24</p><p>25</p><p>26</p><p>27</p><p>28</p><p>29</p><p>30</p><p>31</p><p>32</p><p>33</p><p>34</p><p>35</p><p>36</p><p>37</p><p>38</p><p>39</p><p>40</p><p>41</p><p>42</p><p>43</p><p>44</p><p>45</p><p>46</p><p>47</p><p>48</p><p>49</p><p>50</p><p>51</p><p>52</p><p>53</p><p>54</p><p>55</p><p>56</p><p>57</p><p>58</p><p>59</p><p>60</p><p>61</p><p>62</p><p>63</p><p>64</p><p>65</p><p>66</p></td><td><div><p><code>const</code> <code>int</code>&nbsp; <code>buttonPin = 2;</code></p><p><code>const</code> <code>int</code> <code>ledPin = 13;</code></p><p><code>int</code> <code>buttonPushCounter = 0;</code></p><p><code>int</code> <code>buttonState = 0;</code></p><p><code>int</code> <code>lastButtonState = 0;</code></p><p><code>void</code> <code>setup() {</code></p><p><code>&nbsp;&nbsp;</code><code>pinMode(buttonPin, INPUT);</code></p><p><code>&nbsp;&nbsp;</code><code>pinMode(ledPin, OUTPUT);</code></p><p><code>&nbsp;&nbsp;</code><code>Serial.begin(9600);</code></p><p><code>}</code></p><p><code>void</code> <code>loop() {</code></p><p><code>&nbsp;&nbsp;</code><code>buttonState = digitalRead(buttonPin);</code></p><p><code>&nbsp;&nbsp;</code><code>if</code> <code>(buttonState != lastButtonState) {</code></p><p><code>&nbsp;&nbsp;&nbsp;&nbsp;</code><code>if</code> <code>(buttonState == HIGH) {</code></p><p><code>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</code><code>buttonPushCounter++;</code></p><p><code>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</code><code>Serial.println(</code><code>"on"</code><code>);</code></p><p><code>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</code><code>Serial.print(</code><code>"number of button pushes:&nbsp; "</code><code>);</code></p><p><code>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</code><code>Serial.println(buttonPushCounter);</code></p><p><code>&nbsp;&nbsp;&nbsp;&nbsp;</code><code>} </code><code>else</code> <code>{</code></p><p><code>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</code><code>Serial.println(</code><code>"off"</code><code>);</code></p><p><code>&nbsp;&nbsp;&nbsp;&nbsp;</code><code>}</code></p><p><code>&nbsp;&nbsp;&nbsp;&nbsp;</code><code>delay(50);</code></p><p><code>&nbsp;&nbsp;</code><code>}</code></p><p><code>&nbsp;&nbsp;</code><code>lastButtonState = buttonState;</code></p><p><code>&nbsp;&nbsp;</code><code>if</code> <code>(buttonPushCounter % 4 == 0) {</code></p><p><code>&nbsp;&nbsp;&nbsp;&nbsp;</code><code>digitalWrite(ledPin, HIGH);</code></p><p><code>&nbsp;&nbsp;</code><code>} </code><code>else</code> <code>{</code></p><p><code>&nbsp;&nbsp;&nbsp;&nbsp;</code><code>digitalWrite(ledPin, LOW);</code></p><p><code>&nbsp;&nbsp;</code><code>}</code></p><p><code>}</code></p></div></td></tr></tbody></table>

然后上传代码到 Arduino，并打开串口调试窗口（放大镜图标）。

效果就是，当你每次按下或松开按键开关，都会打印相应的字符串，来显示当前的按键状态。而与此同时，Arduino UNO上的LED，也会在你每按四次按键更新一次状态。

9,992

[![](https://shumeipai.nxez.com/wp-content/uploads/2023/08/pptalk-h100.png)](https://talk.quwj.com/node/arduino "趣小组-Arduino")

  

-   [arduino](https://arduino.nxez.com/tag/arduino)
-   [level2](https://arduino.nxez.com/tag/level2)
-   [开关](https://arduino.nxez.com/tag/%e5%bc%80%e5%85%b3)
-   [按键开关](https://arduino.nxez.com/tag/%e6%8c%89%e9%94%ae%e5%bc%80%e5%85%b3)
-   [教程](https://arduino.nxez.com/tag/%e6%95%99%e7%a8%8b)