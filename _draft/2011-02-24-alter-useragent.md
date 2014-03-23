---
layout: post
title: 修改Useragent在PC上浏览iPad Web应用
categories: [技术]
tags: [useragent, 移动, ios]
---

修改useragent可以在PC机器上浏览ipad web站点，但是有些功能还是不能体验，
比如重力感应，页面从竖屏变成横屏；还有一些网站会自适应宽度，在PC机上看到
的效果和ipad上还是有一些的出入.

以下是修改useragent从而达到在PC机上浏览ipad web站点的设置：
Firefox:

1.在浏览器顶部的的地址栏输入about：config
2.你将看到关于更改的设定的警告，读这些告警，如果你确定继续处理单击继续。
3.点击鼠标右键，选择新建>字符串
4.在弹出的选框中将字符串命名为：general.useragent.override
5.选框会继续要求输入你的字符串的值，复制粘贴下面内容到选框中：Mozilla/5.0 (iPad; U; CPU OS 3_2 like Mac OS X; en-us) AppleWebKit/531.21.10 (KHTML, like Gecko) Version/4.0.4 Mobile/7B334b Safari/531.21.10
6.重启firefox。

这样就可以浏览到ipad版本的web站点了。但是虽然FF设置比较可视化，但是FF浏览器的内核和Safari不一样，显示效果会带来不一样；
我在浏览网易163的ipad版本时就遇到可以成功登录，但是没有邮件数据的情况；经过研究是浏览器的原因，我换用和Safari同样内核的
Chrome谷歌的浏览器显示正常，但是Chrome的启动操作比较麻烦，需要带命令行启动，以下是操作流程:

1.设Chrome的安装目录为${chormedir},我的目录为C:\Users\Lamb\AppData\Local\Google\Chrome\Application\chrome.exe
2.运行cmd，至win下的命令行，chrome.exe --user-agent="*****”，我的命令行为C:\Users\Lamb\AppData\Local\Google\Chrome\Application\chrome.exe --user-agent="Mozilla/5.0 (iPad; U; CPU OS 3_2 like Mac OS X; en-us) AppleWebKit/531.21.10 (KHTML, like Gecko) Version/4.0.4 Mobile/7B334b Safari/531.21.10"
访问http://mail.163.com/ 会自动跳转至 http://ipad.mail.163.com/ 输入用户名 密码 即可登录.