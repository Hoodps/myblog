---
layout: post
title:  "Python while语句"
date:   2015-07-21 09:43:59
author: Hoodps
categories: python
---


Python编程中while语句用于循环执行程序，即使在某一条件下，循坏执行某段程序，以处理需要重复处理的相同任务。基本形式为

	while ():
		···
执行语句可以是单个语句或者语句块，判断条件可以是任意表达式，任意非0、非空的值为true.当判断条件为false时候，循坏结束。

	num  = 0
	while (num < 5):
		print "The num is:",num
		num = num + 1
	print "bye bye"

while语句还有两个重要的命令continue、break来跳出循坏，continue用于跳出该次循坏，break用于退出循坏，此处“判读条件”还可以是常值，表示循坏必定成立

	x = 1
	while (x < 10):
		x += 1
		if x % 2 > 0:
			continue
		print x


	x = 1
	while (1):
		x += 1
		if x  > 10:
			break
		print x


## 无限循环
如果条件判断语句永远为 true，循环将会无限的执行下去，如下实例：

	while (1):
		print 'yes'

## 循环使用 else 语句
在 python 中，for … else 表示这样的意思，for 中的语句和普通的没有区别，else 中的语句会在循环正常执行完（即 for 不是通过 break 跳出而中断的）的情况下执行，while … else 也是一样。

	num = 0
	while (num < 6):
		print num
		num = num + 1
	else:
		print "others"

