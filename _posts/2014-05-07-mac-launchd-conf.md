---
layout: post
title: Mac通过launchd.conf文件进行环境变量的设置
categories: [技术]
tags: [java, maven]
---

在Mac下可以通过往/etc/launchd.conf文件中追加命令去来实现对一些环境变量的设置

	setenv  HOME  /PATH

intellij idea下会默认去读取M2_HOME这个环境变量，可以往/etc/launchd.conf文件中追加命令

	setenv M2_HOME /Users/Lamb/Applications/maven/apache-maven-3.2.1

mac下面安装了最新版本的jdk(如1.8)，但是运行eclipse和idea还是提示需要安装jre,如果点击同意会自动安装一个jre6，安装至下面的路径：

	/System/Library/Java/JavaVirtualMachines/1.6.0.jdk/Contents/Home
	
但是其实不需要安装，只需要设置一下JAVA_HOME环境变量即可，安装最新版本的jdk会被安装至下面的路径：

	/Library/Java/JavaVirtualMachines/jdk1.8.0_05.jdk/Contents/Home
	
可以往/etc/launchd.conf文件中追加命令

	setenv JAVA_HOME /Library/Java/JavaVirtualMachines/jdk1.8.0_05.jdk/Contents/Home
	
如果你安装了苹果提供的jre6，也就是想当于设置了JAVA_HOME为jre6，这样在运行java应用程序（如java ***）或者依赖于java的应用程序（如mvn ***）时，默认使用的是jre6，eclipse和idea的运行是没有问题的，但是运行maven命令行是有可能会出现错误。如果你的maven-compiler-plugin插件中的编译级别高于1.6，比如设置为1.8。但是运行mvn tomcat7:run时maven的jre版本却为1.6,相当于用jre6来运行1.8编译的代码，这肯定会出现一些问题的。这也可以通过上面重新设置JAVA_HOME来解决。