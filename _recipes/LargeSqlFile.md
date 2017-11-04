---
title: 'Mysql导入大Sql文件'
image: true
time: 2
category: Tech
tags: [SQL]
keywords: 大sql文件, mysql
description: Mysql导入大Sql文件'
ingredients:
  -
    name: sql
--- 


昨天，实验室平台的数据直接传给我，大概有5G左右。直接用mysqlwork bench 导入会提示错误，使用命令行导入也会提示错误。

一种方法是配置Mysql的init配置文件。这一种我没有成功。

另一种方法是，直接配置全局变量。

1. 进入mysql:
	
		sudo mysql
	
2. 设置运行的最大大小
	
		mysql>  SET GLOBAL max_allowed_packet=214748;
	
最大大小可根据需求制定，单位为M。

3. 设置等待时间
		
		mysql> SET GLOBAL wait_timeout=100000;
		
4. 退出mysql
	
	quit
	
5. 进入到sql文件所在目录

6. 导入数据

		mysql -h localhost -u root -p -- educoder < dbtrustie-Nov-2.sql

	localhost 服务器地址
	root mysql用户名

	

