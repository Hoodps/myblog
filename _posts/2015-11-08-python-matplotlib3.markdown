---
layout: post
title:  "四.matplotlib 饼状图"
date:   2015-11-07 22:43:22
author: Hoodps
categories: matplotlib
---

饼状图显示一个数据系列中各项的大小与各项总和的比较，
饼状图中的数据点显示为整个饼状图的百分比。
比如十大品牌占市场份额。

	# _*_ coding:utf-8 _*_
	from matplotlib import pyplot as plt 

	#调节图形大小，宽，高
	plt.figure(figsize=(6,9))
	#定义饼状图的标签，标签是列表
	labels = [u'第一部分',u'第二部分',u'第三部分']
	#每个标签占多大，会自动去算百分比
	sizes = [50,40,10]
	colors = ['yellowgreen','red','lightskyblue']
	#将某部分爆炸出来， 使用括号，将第一块分割出来，数值的大小是分割出来的与其他两块的间隙
	explode = (0.05,0,0)

	patches,l_text,p_text = plt.pie(sizes,explode=explode,labels=labels,colors=colors,
	                                labeldistance = 1.1,autopct = '%3.1f%%',shadow = False,
	                                startangle = 90,pctdistance = 0.6)

	#labeldistance，文本的位置离远点有多远，1.1指1.1倍半径的位置
	#autopct，圆里面的文本格式，%3.1f%%表示小数有三位，整数有一位的浮点数
	#shadow，饼是否有阴影
	#startangle，起始角度，0，表示从0开始逆时针转，为第一块。一般选择从90度开始比较好看
	#pctdistance，百分比的text离圆心的距离
	#patches, l_texts, p_texts，为了得到饼图的返回值，p_texts饼图内部文本的，l_texts饼图外label的文本

	#改变文本的大小
	#方法是把每一个text遍历。调用set_size方法设置它的属性
	for t in l_text:
	    t.set_size=(30)
	for t in p_text:
	    t.set_size=(20)
	# 设置x，y轴刻度一致，这样饼图才能是圆的
	plt.axis('equal')
	plt.legend()
	plt.show()

生成的饼状图如下所示
<img src="/assets/plt/pie0.png" style="width: 80%;height:50%">

	# _*_ coding:utf-8 _*_
	import matplotlib.pyplot as plt 

	labels = 'A','B','C','D'
	fracs = [15,30,45,10]

	plt.axes(aspect = 1) #比例为1:1，这个就是一个正圆形

	plt.pie(x = fracs, labels = labels, autopct='%1.1f%%')
	plt.show()

生成的饼状图如下所示
<img src="/assets/plt/pie1.png" style="width: 80%;height:50%">

	# _*_ coding:utf-8 _*_
	import matplotlib.pyplot as plt 

	labels = 'A','B','C','D'
	fracs = [15,30,45,10]

	explode = [0, 0.05, 0.08,0] #使饼块凸出一点

	plt.axes(aspect = 1) #比例为1:1，这个就是一个正圆形

	plt.pie(x = fracs, labels = labels, autopct='%1.1f%%', explode = explode)
	plt.show()

生成的饼状图如下所示
<img src="/assets/plt/pie2.png" style="width: 80%;height:50%">
