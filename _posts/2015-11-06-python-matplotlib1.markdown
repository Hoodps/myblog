---
layout: post
title:  "matplotlib 散点图"
date:   2015-11-06 09:43:22
author: Hoodps
categories: matplotlib
---

散点图显示两组数据的值，每个点的坐标位置由变量的值决定。

由一组不连续的点完成，用于观察两种变量的相关性。

例如身高-体重，温度-纬度等等


	import numpy as np
	import matplotlib.pylot as plt

	heiht = [162,170,182,175,173,165]
	wight = [50,58,80,70,69,55]

	plt.scatter(height, wight)
	plt.show()

生成的散点图如下所示
<img src="/assets/plt/scatrer.png" style="width: 50%;">


