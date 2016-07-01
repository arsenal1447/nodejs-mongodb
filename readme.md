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

![](https://github.com/zxx1988328/nodejs-mongodb/blob/master/img/new_db.png)



创建新表tb1,然后删除掉

	db.createCollection("tb1");
	
	show collections;
	
	db.tb1.drop();
	
	show collections;
![](https://github.com/zxx1988328/nodejs-mongodb/blob/master/img/new_table.png)


## 添加数据


>方法一：db.表名.insert(数据);　　

　　1.从上图操作可以看出，没有去创建“tb1”表，其实通过插入操作也会自动创建

　　2._id，是mongodb自已生成的，每行数据都会存在，默认是ObjectId，可以在插入数据时插入这个键的值(支持mongodb支持的所有数据类型)　　
	
![](https://github.com/zxx1988328/nodejs-mongodb/blob/master/img/insert_data.png)


>方法二：db.表名.save(数据);　　 　　

　　1.从上图操作可以看出，save也可达到insert一样的插入效果

　　2._id可以自已插入

　　3.一个表中不一定要字段都相同

![](https://github.com/zxx1988328/nodejs-mongodb/blob/master/img/save_data.png)



>二者的区别;　 　　

*从图中操作就可以看出，虽然insert和save方法都可以插入数据，当默认的“_id”值已存在时，调用insert方法插入会报错；
	而save方法不会,会更新相同的_id所在行数据的信息*

![](https://github.com/zxx1988328/nodejs-mongodb/blob/master/img/diff_add_data.png)



## 查询　　

	查询表中所有数据：db.表名.find();
	
	按条件查询（支持多条件）：db.表名.find(条件); 
	
	查询第一条（支持条件）：db.表名.findOne(条件);
	
	限制数量：db.表名.find().limit(数量);
	
	跳过指定数量：db.表名.find().skip(数量);


![](https://github.com/zxx1988328/nodejs-mongodb/blob/master/img/select_data.png)


## 比较查询

	大于：$gt
	
	小于：$lt
	
	大于等于：$gte
	
	小于等于：$lte
	
	非等于：$ne

![](https://github.com/zxx1988328/nodejs-mongodb/blob/master/img/compare_data.png)


## 或者：$or in和not in查询(包含、不包含) 
	
	$or
	$in
	$nin

![](https://github.com/zxx1988328/nodejs-mongodb/blob/master/img/or_in_nin_data.png)


## 查询数量：db.表名.find().count();

>排序：db.表名.find().sort({"字段名":1}); 

	1：表示升序  -1：表示降序

>指定字段返回： db.表名.find({},{"字段名":0});　　

	1：返回  0：不返回

![](https://github.com/zxx1988328/nodejs-mongodb/blob/master/img/find_data.png)


## 修改

	前面save在_id字段已存在是就是修改操作，按指定条件修改语法如下

	db.表名.update({"条件字段名":"字段值"},{$set:{"要修改的字段名":"修改后的字段值"}});

![](https://github.com/zxx1988328/nodejs-mongodb/blob/master/img/update_data.png)


## 删除

	db.表名.remove(条件);

![](https://github.com/zxx1988328/nodejs-mongodb/blob/master/img/delete_data.png)



## 存储过程

>创建存储过程：

	db.system.js.save({_id:"存储过程ID", 
	value:function(参数){  
	        -- 逻辑主体; 
	        return 返回; 
	}});

>调用存储过程

	db.eval("存储过程ID()");

![](https://github.com/zxx1988328/nodejs-mongodb/blob/master/img/call_procedure.png)


# 项目开始

	cd nodejs_mongodb 

	npm install mongodb --save-dev	//安装 mongodb 驱动

>--save：将保存配置信息至package.json（package.json是nodejs项目配置文件）；
-dev：保存至package.json的devDependencies节点，不指定-dev将保存至dependencies节点；一般保存在dependencies的像这些express/ejs/body-parser等等。*


## 插入数据成功

![](https://github.com/zxx1988328/nodejs-mongodb/blob/master/img/insert_data_success.png)

## 查询数据

![](https://github.com/zxx1988328/nodejs-mongodb/blob/master/img/app_select.png)