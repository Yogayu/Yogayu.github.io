---
title: '域名绑定'
ref:  vanilla-crescents
image: false
time: 5
category: Tech
tags: [DNS]
ingredients:
  -
    name: Jekyll
  -
    name: DNS
  -
    name: Jekyll
--- 


1. 注册域名
2. 在Jekyll根目录，添加CNAME文件（无文件后缀)，并写入域名，例如：
	
		youxinyu.me

3. 在Godaddy中修改域名解析服务器

![7-31-Domain_Manager](/assets/images/posts/7-31-Domain_Manager.png)

![7-31-Domain_Manager](/assets/images/posts/7-31-Domain_Manager-1.png)

		F1G1NS1.DNSPOD.NET
		F1G1NS2.DNSPOD.NET
	
4. 在DNSPod中添加域名解析

![7-31-dnspod](/assets/images/posts/7-31-dnspod.png)



