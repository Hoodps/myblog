---
layout: post
title:  "python urllib"
date:   2015-10-01 11:43:22
author: Hoodps
categories: python
---



## urllib模块中的方法

1.urllib.urlopen(url[,data[,proxies]])
打开一个url的方法，返回一个文件对象，然后可以进行类似文件对象的操作。

	import urllib
	f = urllib.urlopen('http://www.baidu.com')
	firstLine = f.readline()   #读取html页面的第一行

urlopen返回对象提供方法：

-         read() , readline() ,readlines() , fileno() , close() ：这些方法的使用方式与文件对象完全一样

-         info()：返回一个httplib.HTTPMessage对象，表示远程服务器返回的头信息

-         getcode()：返回Http状态码。如果是http请求，200请求成功完成;404网址未找到

-         geturl()：返回请求的url

