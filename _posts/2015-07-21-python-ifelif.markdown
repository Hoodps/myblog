---
layout: post
title:  "Python 条件语句"
date:   2015-07-21 09:43:59
author: Hoodps
categories: python
---


Python条件语句是通过一条或者多条语句的执行结果(True或者False)来决定执行的代码块。
Python程序语言指定任何非0和非空(null)的值为true，0或者null为false.

	if 条件判断:
		执行语句····
	else:
		执行语句····


	if 条件判断1:
		执行语句1···
	elif 条件判断2:
		执行语句2···
	elif 条件判断3:
		执行语句3···
	else:
		执行语句4···

if 语句的判断条件可以用>（大于）、<(小于)、==（等于）、>=（大于等于）、<=（小于等于）来表示其关系。

	num = 5     
	if num == 3:            # 判断num的值
	    print 'boss'        
	elif num == 2:
	    print 'user'
	elif num == 1:
	    print 'worker'
	elif num < 0:           # 值小于零时输出
	    print 'error'
	else:
	    print 'roadman'     # 条件均不成立时输出


由于 python 并不支持 switch 语句，所以多个条件判断，只能用 elif 来实现，如果判断需要多个条件需同时判断时，可以使用 or （或），表示两个条件有一个成立时判断条件成功；使用 and （与）时，表示只有两个条件同时成立的情况下，判断条件才成功。

	num = 9
	if num >= 0 and num <= 10:    # 判断值是否在0~10之间
	    print 'hello'
	>>> hello		# 输出结果

	num = 10
	if num < 0 or num > 10:    # 判断值是否在小于0或大于10
	    print 'hello'
	else:
		print 'undefine'
	>>> undefine		# 输出结果

	num = 8
	# 判断值是否在0~5或者10~15之间
	if (num >= 0 and num <= 5) or (num >= 10 and num <= 15):    
	    print 'hello'
	else:
	    print 'undefine'
	>>> undefine		# 输出结果

简写if语句
	var = 100 
	 
	if ( var  == 100 ) : print "变量 var 的值为100" 

