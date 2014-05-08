---
layout: post
title: 优雅的卸载Mac默认的Xcode附带的git
categories: [技术]
tags: [git, mac]
---

这里说的优雅的卸载其实不是真正的卸载，而是不用动Xcode附带的git，通过用户~/.bash_profile的文件来优雅的完成。仅仅需要在~/.bash_profile文件后追加如下的导出变量代码即可:

	export GIT_HOME=/usr/local/git
	export PATH=$GIT_HOME/bin:$PATH
	
通git官网下载的mac安装包进行安装，git会被安装到

	/usr/local/git
	
Xcode附带的git被安装到

	/usr/bin
	
不必移动或者删除这里的git版本，仅仅需要更改一下用户下面的~/.bash_profile的文件即可优雅的解决git版本的问题.

如果您非要卸载旧的也可以通过下面的命令来完成

	sudo cd /usr/bin
	sudo mkdir old-git
	sudo mv git* old-git
	ln -s /usr/local/git ./
	
~/.bash_profile文件这个文件除了导出GIT_HOME，也会导出其他的HOME，下面是我常用的一些导出

	export COCOS2DX_ROOT=/Users/Lamb/Applications/cocos2d/cocos2d-x-2.2.1
	export PATH=$COCOS2DX_ROOT:$PATH

	export NDK_ROOT=/Users/Lamb/Applications/android-ndk-r9c
	export ANDROID_NDK_ROOT=/Users/Lamb/Applications/android-ndk-r9c
	export ANDROID_SDK_ROOT=/Users/Lamb/Applications/android-sdk-macosx
	export PATH=$NDK_ROOT:$PATH
	export PATH=$ANDROID_NDK_ROOT:$PATH
	export PATH=$ANDROID_SDK_ROOT:$PATH

	export M2_HOME=/Users/Lamb/Applications/maven/apache-maven-3.2.1
	export PATH=$M2_HOME/bin:$PATH
	export GRADLE_HOME=/Users/Lamb/Applications/gradle/gradle-1.11
	export PATH=$GRADLE_HOME/bin:$PATH

	export MONGO_HOME=/Users/Lamb/Applications/mongodb/mongodb-osx-x86_64-2.6.1
	export PATH=$MONGO_HOME/bin:$PATH