---
layout: post
title:  "python 字典(Dictionary)"
date:   2015-07-20 16:43:59
author: Hoodps
categories: python
---

字典是另一种可变容器模型，且可存储任意类型对象。
字典的每个键值(key=>value)对用冒号(:)分割，每个对之间用逗号(,)分割，整个字典包括在花括号({})中 ,格式如下所示：dic = {key1:value1,key2:value2}
## 访问元组
使用下标索引来访问列表中的值

	>>>tuple1 = (1,23,5,67,8,9,0)
	>>> print tuple1[2]
	5
	>>> print tuple1[1:3]
	(23, 5)
	>>> 

## 更新列表中的值

	>>> list1 = ['hello','world',123,345]
	>>> list2 = [1,23,4,5,6,7,8,9]
	>>> print list1[2]
	123
	>>> list1[2] = 435899
	>>> print list1
	['hello', 'world', 435899, 345]

## 删除列表中的元素 del list[3]

	>>> list3 = ["I", "am","python","oh"]
	>>> print list3
	['I', 'am', 'python', 'oh']
	>>> del list3[3]
	>>> print list3
	['I', 'am', 'python']
	>>> 

## python 列表的常用操作

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



