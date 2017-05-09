---
layout: episode
category: podcast
title: Data Science and Fraud Detection at iZettle
date: 2016-09-06
keywords: [big data, practice, data science, development, fraud detection,machine learning]
producer: worldofpiggy.com
explicit: no
block: not available
duration: "15:01"
length: 15000000
media: https://s3.amazonaws.com/dshpodcast/media/datascience_episode_fraud_detection.mp3
excerpt: Data science is making the difference also in fraud detection. In this episode I have a conversation with an expert in the field, Engineer Eyad Sibai, who works at iZettle, a fraud detection company
comments: true
---


<img src="https://s3.amazonaws.com/dshpodcast/media/cover.jpg" />


Welcome everybody to another episode of data science at home, 
In this episode I am going to talk about data science and fraud detection and 
To do that I am going to have a conversation with an expert in the field, machine learning engineer Eyad Sibai.
Here is the transcript.



**Francesco**
Hi Eyad how are you?

**Eyad**
I am good! Thanks... What about you?


**Francesco**
So Eyad is machine learning engineer at iZettle, and contributor of REP Reproducible Experiment Platform. Let me start from the beginning. Eyad, who are you?

**Eyad**
I am Eyad. I hold a bachelor degree in Computer Engineering and a masters degree in Artificial Intelligence. My first full time job was at the largest oil company in the world, Saudi Aramco, developing geophysical applications to process seismic data. After that, I decided to look for more challenging job. So I moved to Sweden to work for a startup at that time called Campanja, optimizing real time bidding for online advertising specifically for Google Adwords. Then, I decided to join iZettle to fight fraud… reduce financial crimes and make the world a better place!

**Francesco**
That is a stunning progress in your career indeed. 
What is iZettle exactly?

**Eyad**
iZettle is reinventing the banking industry by helping small-business owners live better, work less and earn more. Based in Stockholm, iZettle revolutionized mobile payments in 2010 with the world’s first mini chip card reader and software for mobile devices. Today, small business owners around the world use iZettle’s simple services to improve speed and ease of payments at checkout, business management, sales analytics, customer engagement, and to get funding.


**Francesco**
Do you work in a team of data scientists? 

**Eyad**
Yes I do, but at the same time we work very closely with the risk department. As we are a team within risk department.

**Francesco**
So how are you connected to the fraud detection department? 

**Eyad**
Fraud detection is one of the objectives of the risk department

**Francesco**
Can you give a brief explanation of what fraud detection means? 

**Eyad**
Fraud is criminal deception intended to result in financial or personal gain. What we mean by fraud detection is being able to detect it as early as possible, either before it happens or after it’s been done, but early enough to reduce losses I would say. Losses could be financial or non-financial even.

**Francesco**
I know that for confidentiality reasons I cannot ask you exactly what I would like to know but, what exactly are you detecting? 

**Eyad**
Without going much into details, We try to detect and estimate any risks that affect iZettle the company and its merchants. We try to make sure none of these parties lose money or hurt their reputation or brand. You can think of fraud detection in three different perceptions.
The traditional one is “Fraud is an outlier” and by outlier I mean few and different. This is an assumption that all what we know is that the fraud won’t occur much and it is gonna be different than the norm. In this case you can use unsupervised techniques.
The second perception is that “fraud behavior has occurred before and we know about it”.. This is obviously a supervised learning problem.
The third and last one is that “fraud is a sequence of actions that ends up by gaining a reward or not” this is clearly reinforcement learning problem.
This is mirroring a bit what happens in data science in general. Is it a coincidence or wanted?
Of course the trick is to be able to know when and how to use or combine all these type of perceptions when you are building fraud detection system.


**Francesco**
How much human intervention is there in fraud detection?

**Eyad**
Card Payments is a sensitive field. Stopping a legit user to make a transaction is big no-no for iZettle. We take care of our users and try to assure the quality of our detection system. To ensure that we have to add humans to our detection pipeline. Even though we are confident of our detection system, it is always good to be more sure. 


**Francesco**
Do you think there will ever be the perfect detector any time soon? 

**Eyad**
Define perfect and soon! 

**Francesco**
Makes sense :) Ok let’s be pragmatic. What could happen in 5 years from now in the fraud detection arena?

**Eyad**
I would say there will be perfect detector for the current fraud techniques we face, but at the same time fraudsters are being innovative. As technology is evolving to our benefit… it is evolving towards their benefits too. 
In card payments world, banks and card providers can always try to ensure that the payment is legit, but this adds more friction to the payment process… which will affect the conversion rate of the merchants. Sometimes it is not optimal to have zero risk. No Risk no gain. 

**Francesco**
What are the tools you usually work with? 

**Eyad**
We use Amazon Web Services for our infrastructure. 
For machine learning pipeline… We use apache spark for data processing even though I am fan of dask :) and for the modeling part we use the python package scikit-learn with some of our in-house tools.


**Francesco**
Eyad, this is a question I have been asking around and I have also been asked. 
Why Python? 

**Eyad**
Python now is the most popular introductory teaching language in Top U.S universities… used to be java.Also it is being a replacement for matlab for engineers and scientists. Numpy is very close to how to use matlab arrays. Matplotlib interface is very close to matlab plotting.In addition, python is free and open source…


**Francesco**
Absolutely correct, as we have seen matlab going really down and have basically no position in the data analytics field so far. Not true for pure engineering applications though.
 
**Eyad**
Check Amazon Web Services or Google Cloud Platform or any other cloud service provider, they always have a python api for their service. These days,  It is almost always java api and python API.
I do believe Python’s readability is the no. 1 reason for why python.  The second reason is the rich packages and libraries that are ready to use in python like Pandas… Scikit-learn… and others… So I would ask non python developers … why not python.



**Francesco**
And now let’s move to REP, which stands for Reproducible Experiment Platform.
From the github repo I read the usual description “REP is environment for conducting data-driven research in a consistent and reproducible way.” 
What is that? 

**Eyad**
It is a framework that provides you with sklearn-like interface or wrapper to many machine learning packages scikit-learn, xgboost, pybrain … and others. The aim of the package is to solve one of the hardest problems in research connected to data. It comes with tools and a docker image to be able to reproduce your research, models, or conclusions about data.
which means that you can reproduce an experiment anytime, within any environment, in exactly the same conditions it was performed the first time?


**Francesco**
How mature this project is?

**Eyad**
I would say it is mature enough. With these type of projects you can always ask for more. It is never ending project. Maturity is a relative thing not easy to measure :)


**Francesco**
As a data scientist, why should I be interested in such a platform? 

**Eyad**
REP comes with fantastic tooling. The sklearn-like wrapper over many different machine learning packages, Classification report and regression report which includes many interesting plots like learning curve, features distributions and correlations, features importance and many more. You can train and test many classifiers in parallel and do comparisons between them. It is really a neat project.


**Francesco**
What is your contribution within the project?

**Eyad**
My contribution was mainly making it possible to use it with python3 as it didn’t support python3. 


**Francesco**
Where do u see data science in 10 years

**Eyad**
In 10 years, the competition will be more into who has a better data quality. With deep learning, the challenge is becoming more into data quality and quantity. We can read these days many slogans that support this conclusion “data is the new oil”, environmentally friendly people say  “data is the new bacon”,  and vegetarians or vegans “data is the new tofu”.  


**Francesco**
What about deep learning techniques?

**Eyad**
I don’t think it will be only limited to deep learning techniques. Also, I believe we will see a collection of tools and services that will simplify our day to day tasks as data scientists. In addition, there will be high demand for data scientists. every  company will hire data scientists to mine their data. 


**Francesco**
How about data science in the near future?

**Eyad**
Nowadays we see new startups trying to build automated machine learning as a service. I do believe this will have great future but it won’t solve all problems. Companies nowadays are being more aware about data and its value. If they don’t start collecting and quality assure the data, they will regret it big times. 
Remember, “ With data collection, ‘the sooner the better’ is always the best answer”



**Francesco**
Eyad it was nice to have you here at Data science at home.
I truly enjoyed and I hope that our listeners did as well. I am looking forward to seeing the progress we expect on Reproducible Experiment Platform and of course good luck detecting bad guys!

**Eyad**
Thank you! 

