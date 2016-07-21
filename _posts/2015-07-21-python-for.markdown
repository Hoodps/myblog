---
layout: post
title:  "python for循坏"
date:   2015-07-21 10:43:59
author: Hoodps
categories: python
---

Python for循环可以遍历任何序列的项目，如一个列表或者一个字符串。

格式如下：
	for iterating in sepuence:
		····


	for l in "python":
		print l

	lists = ['blue','red','green']
	for color in lists:
		print color

## 通过序列索引迭代
另外一种执行循环的遍历方式是通过索引，如下实例：

	lists = ['blue','red','green']
	for i in range(len(lists)):
		print lists[i]

## 循环使用 else 语句
在 python 中，for … else 表示这样的意思，for 中的语句和普通的没有区别，else 中的语句会在循环正常执行完（即 for 不是通过 break 跳出而中断的）的情况下执行，while … else 也是一样。
如下实例：

	# _*_ coding:utf-8 _*_
	for num in range(10, 20): # 迭代 10 到 20 之间的数字
		for i in range(2, num):
			if num % i == 0:
				j = num / i
				print '%d 等于 %d * %d' % (num, i, j)
				break
		else:
			print num,'是质数'
