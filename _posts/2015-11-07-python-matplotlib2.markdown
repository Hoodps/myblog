---
layout: post
title:  "三.matplotlib 折线图"
date:   2015-11-07 22:43:22
author: Hoodps
categories: matplotlib
---

折线图是用直线段将各数据连续起来组成的图形。

常用来观察数据随时间变化的趋势。

例如股票价格、温度变化等等。


	import numpy as np
	import matplotlib.pyplot as plt

	x = np.linspace(-10, 10, 100)
	y = x ** 2
	plt.plot(x, y)
	plt.show()

生成的散点图如下所示
<img src="/assets/plt/plot1.png" style="width: 80%;height:50%">

	import numpy as np
	import matplotlib.pyplot as plt
	import matplotlib.dates as mdates

	date,open,close = np.loadtxt('table.csv', delimiter=',', 
	converters={0:mdates.strpdate2num('%Y-%m-%d')},skiprows=1,
	usecols=(0,1,4),unpack=True)
	#plt.plot(date,open)

	plt.plot_date(date,open,'-')
	plt.show()

生成的散点图如下所示
<img src="/assets/plt/plot2.png" style="width: 80%;height:50%">
