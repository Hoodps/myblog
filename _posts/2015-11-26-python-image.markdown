---
layout: post
title:  "破解验证码"
date:   2015-11-26 22:43:22
author: Hoodps
categories: python
---

本实验将通过一个简单的例子来讲解破解验证码的原理。

	#-*- coding:utf8 -*-
	from PIL import Image

	im = Image.open("captcha.gif")
	#(将图片转换为8位像素模式)
	im.convert("P")

	#打印颜色直方图
	print im.histogram()


简单线性回归

	import numpy as np

	def fitSLR(x, y):
	    n = len(y)
	    dinominator = 0
	    numerator = 0

	    for i in range(0, n):
	        numerator += (x[i] - np.mean(x)) * (y[i] - np.mean(y))
	        dinominator += (x[i] -np.mean(x)) ** 2
	    print "numerator:", numerator
	    print "dinominatro:", dinominator

	    b1 = numerator / float(dinominator)
	    b0 = np.mean(y) / float(np.mean(x))

	    return b0, b1
	    
	def predict(x, b0, b1):
	    return b0 + x * b1



	x = [1, 3, 2, 1, 3]
	y = [14, 24, 18, 17, 27]

	b0, b1 = fitSLR(x, y)

	print "b0:", b0
	print "b1:", b1

	a = predict(6, b0, b1)
	print a

多元线性回归

	import numpy as np
	from sklearn import linear_model

	data = np.array([
	    [100, 4, 9.3],
	    [50, 3, 4.8],
	    [100, 4, 8.9],
	    [100, 2, 6.5],
	    [50, 2, 4.2],
	    [80, 2, 6.2],
	    [75, 3, 7.4],
	    [65, 4, 6],
	    [90, 3, 7.6],
	    [90, 2, 6.1]])

	x = data[:, :-1]
	y = data[:, -1]

	regr = linear_model.LinearRegression()
	regr.fit(x, y)
	xPred = [102, 6]

	yPred = regr.predict((xPred))
	print yPred


非线性回归

	import numpy as np
	import random

	def gradientDescent(x, y, theta, alpha, m, numIterations):
	    xTrans = x.transpose()
	    print numIterations
	    for i in range(0, numIterations):
	        hypothesis = np.dot(x, theta)
	        loss = hypothesis - y

	        cost = np.sum(loss ** 2) / (2 * m)
	        print ("Iteration %d / Cost: %f" % (i, cost)) 

	        gradient = np.dot(xTrans, loss) / m
	        theta = theta - alpha * gradient
	    return theta


	def getData(numPoints, bias, veriance):
	    x = np.zeros(shape=(numPoints, 2))
	    y = np.zeros(shape=numPoints)

	    for i in range(0, numPoints):
	        x[i][0] = 1
	        x[i][1] = i

	        y[i] = (i + bias) + random.uniform(0, 1) * veriance
	    return x, y

	x, y = getData(100, 25, 10)

	m, n = np.shape(x)
	n_y = np.shape(y)

	numIterations = 100000
	alpha = 0.0005
	theta = np.ones(n)

	theta = gradientDescent(x, y, theta, alpha, m, numIterations)
	print theta

