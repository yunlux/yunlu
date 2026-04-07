---
{"dg-publish":true,"dg-permalink":"fadanmu","permalink":"/fadanmu/","created":"2024-07-10T16:05:39.579+08:00","updated":"2024-08-11T21:45:06.469+08:00","dg-note-properties":{}}
---



使用浏览器（Microsoft Edge浏览器 或者 360安全浏览器）进入B站直播间 登录好账号后 按键盘上的 F12→控制台（Console）→鼠标点最下面的>后面 复制粘贴下面的命令 回车，取消挂机代码刷新页面即可。

注意，新版chrome需要在粘贴前手动输入**允许粘贴**并回车

```JavaScript

var str = window.prompt("请输入循环的命令,多个命令以空格分割","加入 攻击 突破 摸索");
if (str != null && str != ""){
    var strList = str.split(' ')
    var interval = window.prompt("请输入循环的命令（以秒为单位，最低为5秒）：",10);
		var count = 0
    var Max = strList.length
  	if (interval < 5){
      interval = 5
    }
    var timer = setInterval(() => {
        var dom = document.querySelectorAll("textarea.chat-input.border-box")[0];
        var evt = new InputEvent('input', {
            inputType: 'insertText',
            data: 'insertText',
            dataTransfer: null,
            isComposing: false
        });
        dom.value = strList[count];
        dom.dispatchEvent(evt);
        setTimeout(() => {
            document.querySelectorAll("button.bl-button.live-skin-button-text")[0].click();
        }, 100);
				count++;
      	if(count >= Max){
          count = 0;
        }
    }, 1000*interval);
}

```
