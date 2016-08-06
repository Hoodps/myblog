---
layout: post
title:  "一.numpy 基础"
date:   2015-11-06 08:43:22
author: Hoodps
categories: matplotlib
---

numpy是python的开源数值计算的拓展，可以用来存储和处理大型矩阵，比python自身的数据结构更加高效。Numpy将python变成了一种免费强大的Matlab系统。

## ndarray对象

1.从python的基础数据转化为ndarray对象

	import numpy as np
	a = [2,34,5,67,8,]  #python的列表
	a
	[2, 34, 5, 67, 8]

	a1 = np.array(a) #转换为ndarray对象
	a1
	array([ 2, 34,  5, 67,  8])
	type(a1)
	numpy.ndarray

2.用numpy直接生成ndarray对象

	import numpy as np
	b = np.arange(11) #arange()方法可以生成数列
	b
	array([ 0,  1,  2,  3,  4,  5,  6,  7,  8,  9, 10])

3.从文件读取数据

	import numpy as np
	a = np.loadtxt('table.csv', delimiter=',', skiprows=1,usecols=(1,2,3),unpack=True)
	a.shape # 数组大小
	(3, 6648)


	b = np.arange(10)
	b
	array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])
	b * b # 矩阵乘法
	array([ 0,  1,  4,  9, 16, 25, 36, 49, 64, 81])
	b + b #矩阵加法
	array([ 0,  2,  4,  6,  8, 10, 12, 14, 16, 18])

4.索引和切片

	b = np.arange(10)
	b[3]
	3
	b[-1]
	9
	b[0:5]
	array([0, 1, 2, 3, 4])
	b[:5]
	array([0, 1, 2, 3, 4])
	b[::2]
	array([0, 2, 4, 6, 8])

## 常用函数

在numpy调用函数有两种方法
1.np.func(a)
2.a.func() #因为ndarray 本身就是一个对象

	c = np.random.randint(1, 100, 10)
	c
	array([ 1,  3, 65, 67, 19, 71, 59,  2, 69, 13])
	c.min()
	1
	np.min(c)
	1
	np.max(c)
	71
	np.mean(c) #平均值
	36.899999999999999

排序

	>>> x = np.random.randint(1, 100, 10)
	>>> x
	array([16, 36, 40, 94, 22, 32, 11, 27, 17, 98])
	>>> y = np.sort(x)
	>>> y
	array([11, 16, 17, 22, 27, 32, 36, 40, 94, 98])
	>>> x
	array([16, 36, 40, 94, 22, 32, 11, 27, 17, 98])
	>>> 
	>>> y = x.sort()  
	>>> y #y 没有值
	>>> x #但是x已经被排序了
	array([11, 16, 17, 22, 27, 32, 36, 40, 94, 98])
	>>> 
