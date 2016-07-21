---
layout: post
title:  "python 列表(List)"
date:   2015-07-20 09:43:59
author: Hoodps
categories: python
---

列表是最常用的Python数据类型，它可以作为一个方括号内的逗号分隔值得出现。
list = [1,2,3,4],列表可变

## 访问列表中的值
使用下标索引来访问列表中的值

	>>> list1 = ['hello','world',123,345]
	>>> list2 = [1,23,4,5,6,7,8,9]
	>>> print list1[1]
	world
	>>> print list2[2:5]
	[4, 5, 6]

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



