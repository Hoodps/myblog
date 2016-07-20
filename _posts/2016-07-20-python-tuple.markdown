---
layout: post
title:  "python 元组(Tuple)"
date:   2015-07-20 15:43:59
author: Hoodps
categories: python
---

Python的元组与列表类似，不同之处在于元组的元素不能修改。
元组使用小括号，列表使用方括号。
元组创建很简单，只需要在括号中添加元素，并使用逗号隔开即可
例如：t = (1,234,5,65,78)
## 访问元组
使用下标索引来访问列表中的值

	>>>tuple1 = (1,23,5,67,8,9,0)
	>>> print tuple1[2]
	5
	>>> print tuple1[1:3]
	(23, 5)
	>>> 

## 更新列表中的值

	>>> tuple2 = (23,34,456,57)
	>>> tuple3 = ('this','is','a','tuple')
	>>> tuple4 = tuple2 + tuple3
	>>> print tuple4
	(23, 34, 456, 57, 'this', 'is', 'a', 'tuple')

	>>> tuple2[3] = 3478  #这样修改会保存
	Traceback (most recent call last):
	  File "<stdin>", line 1, in <module>
	TypeError: 'tuple' object does not support item assignment

## 删除列表中的元素 del list[3]

	>>> del tuple2
	>>> print tuple2
	Traceback (most recent call last):
	  File "<stdin>", line 1, in <module>
	NameError: name 'tuple2' is not defined
	>>> del tuple3[0]
	Traceback (most recent call last):
	  File "<stdin>", line 1, in <module>
	TypeError: 'tuple' object doesn't support item deletion

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



