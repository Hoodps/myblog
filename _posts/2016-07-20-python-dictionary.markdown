---
layout: post
title:  "python 字典(Dictionary)"
date:   2015-07-20 16:43:59
author: Hoodps
categories: python
---

字典是另一种可变容器模型，且可存储任意类型对象。
字典的每个键值(key=>value)对用冒号(:)分割，每个对之间用逗号(,)分割，整个字典包括在花括号({})中 ,格式如下所示：dic = {key1:value1,key2:value2}

## 访问字典
使用下标索引来访问列表中的值

	>>> dict1 = {'name':'hoodps','age':22,'class':'test'}
	>>> print dict1['name']
	hoodps
	>>> print dict1['age']
	22
	>>> 
	>>> print dict1['test']
	Traceback (most recent call last):
	  File "<stdin>", line 1, in <module>
	KeyError: 'test'

## 更新字典中的值

	>>> print dict1
	{'age': 22, 'name': 'hoodps', 'class': 'test'}
	>>> dict1['age'] = 32
	>>> print dict1
	{'age': 32, 'name': 'hoodps', 'class': 'test'}

## 删除字典中的元素
能删单一的元素也能清空字典，清空只需一项操作。
显示删除一个字典用del命令，如下实例：
	>>> print dict1
	{'age': 32, 'name': 'hoodps', 'class': 'test'}
	>>> del dict1['name']
	>>> print dict1
	{'age': 32, 'class': 'test'}
	>>> dict1.clear
	<built-in method clear of dict object at 0x10fc8a050>
	>>> dict1.clear()
	>>> print dict1
	{}
## python 字典的常用操作

	>>> len(list3) #列表的长度
	3
	>>> list4 = [2,3,4,5] + [6,7,8,9] #列表组合
	>>> print list4
	[2, 3, 4, 5, 6, 7, 8, 9]
	>>> list5 = ['yes'] * 4 #列表相乘
	>>> print list5
	['yes', 'yes', 'yes', 'yes']
	>>> 6 in list4 #判读元素是否在类表中
	True



