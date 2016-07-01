study url:[http://www.cnblogs.com/zhongweiv/p/node_mongodb.html](http://www.cnblogs.com/zhongweiv/p/node_mongodb.html)




## 运行环境 

>windows:需要安装 mongodb 客户端


## windows运行 mongodb

	mongo

![cmd_start](https://github.com/zxx1988328/nodejs-mongodb/blob/master/img/cmd_start.png)

	MongoDB默认端口是27017，可以修改！ 

	对于“E:\Program Files\MongoDB\Server\3.0\bin”目录下的exe程序，做个简单的说明，可能更利于了解可以做些什么操作，基础学习关注mongod.exe和mongo.exe即可
	
	mongo.exe：客户端，支持js语法
	
	mongod.exe：服务端
	
	mongodump.exe：备份工具
	
	mongorestore.exe：恢复工具
	
	mongoexport.exe：导出工具
	
	mongoimport.exe：导入工具
	
	mongostat.exe：实时性能监控工具
	
	mongotop.exe：跟踪MongDB实例读写时间工具


　　*更多详细解释或操作可以查看：http://docs.mongodb.org/manual/reference/program/*

**cd nodejs_mongodb 项目 执行**

创建新的数据库zxxdb1

	use zxxdb1;
	db.movie.insert({"name":"zxx"});//必须对数据库操作,才可以显示出该数据库
	show dbs;

![](https://github.com/zxx1988328/nodejs-mongodb/blob/master/img/add_db.png)



创建新表tb1,然后删除掉

	db.createCollection("tb1");
	
	show collections;
	
	db.tb1.drop();
	
	show collections;
![](https://github.com/zxx1988328/nodejs-mongodb/blob/master/img/123.png)


