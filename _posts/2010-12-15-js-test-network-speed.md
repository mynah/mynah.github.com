---
layout: post
title: javascript网络测速
categories: [技术]
tags: [javascript, 测速]
---

	//图片大小  单位kb
	var filesize = 126.0 
	var sum=0;
	var n=0;
	var starttime;
	$(document).ready(function(){
	    timedCount();
	    });
	function getVelocity(timestamp) {
	    var endtime = new Date();
	    var speed = formatFloat(Math.round(filesize * 1024) / (endtime - starttime),2);    //得到网速 kb/s  
	    sum+=speed;n++;
	    var averagespeed=formatFloat(sum/n,2);
	    $(".speed").val(speed);
	    $(".averagespeed").val(averagespeed);
	    $("#"+timestamp).remove();          
	}
	function timedCount()
	{      
	    var nowtime = new Date();
	    var timestamp = nowtime.getTime();
	    var imgsrc = "http://hiphotos.baidu.com/baidu/pic/item/da6c6827187c9620908f9d2b.jpeg?timestamp="+timestamp;
	    var imgtag = "<img id=""+timestamp+"" src="http://lamb.b3log.org/"+imgsrc+"" alt="" width="0" height="0">";
	    //alert(imgtag);
	    starttime = new Date();
	    $(imgtag).appendTo("body");
	    var testspeed = setTimeout("timedCount()",1000)
	}
	function formatFloat(src, pos)
	{
	     return Math.round(src*Math.pow(10, pos))/Math.pow(10, pos);
	}