---
layout: post
title: Mongdb后台daemon方式启动与停止
categories: [技术, 数据库]
tags: [mongodb, nosql]
---

在后台开启Mongdb服务可以使用--fork。启用fork必须要带上--logpath来指定日志输出目录。为了防止日志被覆盖可以开启--logappend。

	mongod --fork --logpath /data/log/20140407.log --logappend
	
mongodb默认的数据保存路径是/data/db/，默认端口号为27017。如果想修改可以使用--dbpath和--port来修改

	mongod --dbpath /mydata/ --port 20111
	
也可以把参数写入配置文件中，通过配置文件来启动。

	mongod -f /data/conf/mongodb.conf
	
配置文件如下：

	port = 27017
	dbpath = /data/db
	logpath = /data/log/20140407.log
	logappend = true
	fork = true

如果没有使用--fork，退出终端的时候mongodb会自动清理退出，把没有写好的数据写完成，并最终关闭数据文件。要注意的是这个过程会持续到所有操作都完成。如果使用--fork在后台运行mongdb服务，那么就要通过向服务器发送shutdownServer()消息来关闭。

	use admin
	db.shutdownServer()
	
要注意的是，这个命令只允许在本地，或是一个经过认证的客户端。

如果这是一个主从式的复制集群，在1.9.1版本后将按下面的步骤来关闭

* 检查从Mongodb的数据更新时间
* 如果所有的从Mongodb和主的时间差都超过10，这个时候不会关闭mongodb（在这种情况下面，我们可以通过配置timeoutSecs的方式来让从Mongodb完成数据的更新）
* 如果其中有一个从Mongodb与主服务时间差在10秒内，那么主服务器将会关闭，并且等待从Mongodb更新完成并关闭。

如果没有up-to-date 从Mongodb且你想强制关闭服务，可以通过添加force:true;命令如下：

	db.adminCommand({shutdown : 1, force : true})
	or
	db.shutdownServer({force : true, timeoutsec : 5})
	
Window下面以后台服务的方式启动可以使用下面的命令添加服务，配置文件的内容同mac下的

	sc create MongoDB binPath= "\"%MONGO_HOME%\bin\mongod.exe\" --service --config=\"%MONGO_HOME%\mongod.cfg\"" DisplayName= "MongoDB" start= "auto"

如果成功看到

	[SC] CreateService SUCCESS

服务安装成功后可以使用命名启动也可以手动启动

	net start MongoDB

想删除服务可以使用如下命令

	sc delete "MongoDB"

