---
layout: post
title:  "knn"
date:   2015-11-25 22:43:22
author: Hoodps
categories: matplotlib
---

knn算法

	#_*_ coding:utf-8 _*_
	import csv
	import random
	import math
	import operator

	'''
	读取数据
	'''
	def loadDataset(filename, split, trainingSet = [], testSet = []):
		with open(filename, 'rb') as csvfile:
			lines = csv.reader(csvfile)
			dataset = list(lines)

			for x in range(len(dataset) - 1):

				for y in range(4):
					dataset[x][y] = float(dataset[x][y])

				if random.random() < split:
					trainingSet.append(dataset[x])
				else:
					testSet.append(dataset[x])


	def euclideanDistance(instance1, instance2, lenght):
		distance = 0
		for x in range(lenght):
			distance += pow((instance1[x] - instance2[x]), 2)
		return math.sqrt(distance)

	def getNeighbors(trainingSet, testInstance, k):
		distances = []
		lenght = len(testInstance) - 1
		for x in range(len(testInstance)):
			dist = euclideanDistance(testInstance, trainingSet[x], lenght)
			distances.append((trainingSet[x], dist))
		distances.sort(key=operator.itemgetter(1))
		neighbors = []
		for x in range(k):
			neighbors.append(distances[x][0])
		return neighbors


	def getResponse(neighbors):
		classVotes = {}
		for x in range(len(neighbors)):
			response = neighbors[x][-1]
			if response in classVotes:
				classVotes[response] += 1
			else:
				classVotes[response] = 1

		sortedVotes = sorted(classVotes.iteritems(), key=operator.itemgetter(1),reverse=True)
		return sortedVotes[0][0]


	def getAccuracy(testSet, predictions):
		correct = 0
		for x in range(len(testSet)):
			if testSet[x][-1] == predictions[x]:
				correct += 1
		return (correct/float(len(testSet))) * 100.0




	def main():

		trainingSet = [] #训练集
		testSet = [] #测试集
		split = 0.67 #

		#加载数据
		loadDataset(r'is.txt', split, trainingSet, testSet)



		print 'train set:' + repr(len(trainingSet))
		print 'Test set:' + repr(len(testSet))
		#print testSet
		predictions = []
		k = 3

		# for x in range(len(testSet)):
		# 	nerghbors = getNeighbors(trainingSet, testSet[x], k)
		# 	result = getResponse(nerghbors)
		# 	predictions.append(result)
		# 	print ('>predicted='+repr(result) +',actual='+repr(testSet[x][-1]))

		# accuracy = getAccuracy(testSet, predictions)
		# print ('Accutacy:' + repr(accuracy) + '%')


	main()
  