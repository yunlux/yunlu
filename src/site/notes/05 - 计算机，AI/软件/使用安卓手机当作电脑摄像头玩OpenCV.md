---
{"dg-publish":true,"permalink":"/05-ai//open-cv/","created":"2024-08-04T12:27:05.812+08:00","updated":"2024-08-04T12:30:58.903+08:00"}
---





鉴于一些小伙伴没有摄像头，无法愉快地玩耍人脸识别等高科技，特意找到这个方法。

手机上安装这个app:

DroidCam.apk

获取摄像头的代码改成这样：


```python
# cap = cv2.VideoCapture(0)

cap = cv2.VideoCapture("http://192.168.2.52:4747/mjpegfeed?640x480")

```


具体的网址因人而异，获取方法：

浏览器输入手机上显示的Browser IP Cam Access地址

例如我的是 [http://192.168.2.52:4747](http://192.168.2.52:4747)

再如图点击info图标即可获取视频流地址

![0ea6e1aa-2a41-4950-bba7-1af106c64824.jpg](/img/user/05%20-%20%E8%AE%A1%E7%AE%97%E6%9C%BA%EF%BC%8CAI/files/0ea6e1aa-2a41-4950-bba7-1af106c64824.jpg)

![2da6b105-fd4b-4ad0-a4d3-1b1de19c1a32.jpg](/img/user/05%20-%20%E8%AE%A1%E7%AE%97%E6%9C%BA%EF%BC%8CAI/files/2da6b105-fd4b-4ad0-a4d3-1b1de19c1a32.jpg)


> 这个是通过wifi传输的视频流，试了下USB并不能成功连接，可能是win10系统的问题。  
> 不过wifi已经很流畅清晰，延迟也可以接受。  
> 另外还可以在手机上点击HD图标切换到720p模式。