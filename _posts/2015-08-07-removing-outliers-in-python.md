---
layout: post
title: Removing outliers in Python
tags: [analytics, bigdata, coding, computation, filtering, outlier, python, scipy]
comments: true
---


In the attempt of removing outliers from a list of numbers without getting
stuck on too much theory, I would like to share a fast solution that seems to
work quite effectively (at least on the data at hand). 

Here is a quite effective snippet that does the job. 
Don't forget to comment, like, share, etc.

<img src="http://worldofpiggy.com/wp-content/uploads/2015/08/plot.png" />

	import matplotlib.pyplot as plt import scipy.signal as sps
	raw = np.zeros(100) # create some outliers raw[54:57] = 1
	raw[23:24] = 1 
	raw[91] = -1 
	raw[76:80] = -1 # too big to be outlier 
	figure(1)
	plt.plot(raw, 'bo', label='raw data') # filter outliers 
	filtered = sps.medfilt(raw, kernel_size=7) 
	plt.plot(filtered, 'r', label='Filtered profile') axis([0, len(raw), -1.5, 1.5]) 
	plt.legend(loc=3, ncol=2, borderaxespad=0.) 
	#plt.show() 
	savefig('plot.png') 
	
You can also 
[download](https://github.com/worldofpiggy/python-code/blob/master/removeOutliers.py) it from my [Github](https://github.com/worldofpiggy) account. 

Happy filtering!

