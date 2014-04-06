---
layout: post
title: Hello Node.js
categories: [技术, nodejs]
tags: [nodejs]
---

<p><img src="http://nodejs.org/logo.png" alt="nodejs" width="420" height="111"></p>
#Node.js

这里是官网：[http://nodejs.org](http://nodejs.org)

#安装

要使用Node.js,首先需要进行安装。关于如何安装Node.js，这里就不赘述了，可以直接参考官方的安装指南。

#“Hello World”

好了，“废话”不多说了，马上开始我们第一个Node.js应用：“Hello World”。

打开你最喜欢的编辑器，创建一个helloworld.js文件。我们要做就是向控制台或命令行输出“Hello World”，如下是实现该功能的代码：

	console.log("Hello World");
保存该文件，并通过Node.js来执行：
node helloworld.js		
正常的话，就会在终端输出Hello World
Hello world太简单？那来点复杂的！

	var Buffer = require('buffer').Buffer,
	buf = new Buffer(256),
	len = buf.write('\u00bd + \u00bc = \u00be', 0);
	console.log(len + " bytes: " + buf.toString('utf8', 0, len));

不用管什么意思，拷贝执行，感受一下就可以！

#HTTP

如果启动一个http服务呢？嗯，很简单！来感受一下在浏览器中看到hello world。

	var http = require('http');
	http.createServer(function (req, res) {
	  res.writeHead(200, {'Content-Type': 'text/plain'});
	  res.end('Hello World ');
	}).listen(80);
	console.log('Server is running');

#END

入门结束