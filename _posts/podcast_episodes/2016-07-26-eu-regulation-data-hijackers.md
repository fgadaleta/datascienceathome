---
layout: episode
category: podcast
title: EU Regulations and the rise of Data Hijackers
date: 2016-07-26
keywords: [big data, correlation, data science, EU, law,legal,machine learning,regulation]
producer: worldofpiggy.com
explicit: clean
block: not available
duration: "16:17"
length: 14900000
media: https://s3.amazonaws.com/dshpodcast/media/datascience_episode_15_GDPR.mp3
excerpt: Extracting knowledge from large datasets with large number of variables is always tricky. Dimensionality reduction helps in analyzing high dimensional data, still maintaining most of the information hidden behind complexity. Here are some methods that you must try before further analysis (Part 1).
comments: true
---


<img src="https://s3.amazonaws.com/dshpodcast/media/cover.jpg" />



The subject of this episode is about a recent regulation that is being considered by EU that needs the attention of experts in data analytics and machine learning.

Data scientists are cool! And data science as machine learning is just an awesome field that many times, especially in the last few years is achieving goals that are more magical than real.
The improvements of data science in several domains are just impressive.

We’re not far from the first reliable self driving vehicle being it a car, that can deal with realistic urban scenarios. Then there will be self driving cabs, buses, trains and who knows maybe planes and boats.

We can already predict quite accurately if we might be interested in purchasing this or that book, connect to this or that person to engage amazing conversations because they share our personal interests.

We can already support decisions of medical doctors in predicting certain diagnoses (and in some cases algorithms can be scarily accurate, think of fMRI or cancer imaging). I was personally involved in the Non Invasive Prenatal Testing – to detect chromosomal aberrations of the fetus from DNA data analysis. For specific genetic disorders and under specific conditions the accuracy can be higher than 97%. This is what I mean by scarily accurate!

Maybe the chances that you are protecting the interests of a financial institution are not that high, but would you like to know in advance if families can pay back their loan, in order to minimize the risks for both?

All of this can be illegal, in just less than 2 years.



According to a EU regulation that will take place in April 2018, it has been decided that algorithms that make decisions based on user-level predictors which “significantly affect” users, should be regulated. We will go to the details of what significantly affect means.

In addition, they also introduce the “right to explanation” for users who can ask for an explanation of an algorithmic decision that was made about them.

The first part of the regulation literally declares as out of law, many important algorithms that are currently used, eg. recommendation systems, algorithms for credit and insurance risk assessments, computational advertising, and social networks.

The second part is somehow impossible to guarantee. Namely, explaining a decision is usually equivalent to fully understanding an algorithm. Which can be possible only in few cases.

What about deep learning and neural networks? How can we explain what is notoriously known to be a black box? How about probabilistic approaches that make decisions that are only probabilistically stable/valid? Think about methods that use sampling, or MCMC methods in which there is an important random component.

Maybe the only algorithms that can be easily explained are linear regression and decision trees, to name a few, that are heavily based on the concept of correlation and trend analysis. This still does not explain causality however. We will get back to this concept later.

Here is an excerpt of the General Data Protection Regulation (GDPR)

**Article 11. Automated individual decision making**

    Member States shall provide for a decision based solely on automated processing, 
    including profiling, which produces an adverse legal effect concerning the data 
    subject or significantly affects him or her, to be prohibited unless authorised 
    by Union or member State law to which the controller is subject and which  provides 
    appropriate safeguards for the rights and freedoms of the data subject, at least 
    the right to obtain human intervention on the part of the controller.

 

Paragraph 1 prohibits any “decision based solely on automated processing,  including  profiling”  which  “significantly  affects” a data subject.
That is? Trying to quantifying something with qualitative terminology never ends well. So let’s assume we are studying an individual who is 80% healthy and an algorithm that might observe  many more variables a medical doctor can, assess that the individual is a bit less than 70% healthy. Is this 10% significantly affecting the person?

Now let’s get to the word profiling.

Profiling is  “a  form  of  automated  processing  of personal data consisting of the use of personal data to evaluate certain personal aspects relating to a natural person” (a trivial correlation analysis, or variable selection procedure that focuses on certain variables related to the single person, can be considered profiling)

    Decisions referred to in paragraph 1 of this Article shall not be based on special 
    categories of personal data referred to in Article 10, unless suitable measures to 
    safeguard the data subject’s rights and freedoms and legitimate interests are in place.

Ok basically this paragraph prohibits automated processing “based on special categories of personal data”

    Profiling that results in discrimination against natural persons on the basis of 
    special categories of personal data referred to in Article 10 shall be prohibited, 
    in accordance with Union law.

And about discrimination we can start a long discussion because this is here infeasibility kicks in.

Discrimination in very general terms can be defined as the unfair treatment of an individual because of his or her membership in a particular group, belonging to a specific race, having specific gender, or political view or religion etc.

Whenever we use algorithmic profiling for the allocation of resources is, we are implicitly discriminating. Actually that is exactly what we want. Think about clustering or classification. We want to understand if an object or a person belong to a group or another.

I don’t say anything disruptive here if I claim that machine learning depends upon data that has been collected from physical phenomena or society, and as long as society contains inequality, or traces of discrimination, so too will the data.

    Discrimination in machine learning is an asset. Not a problem.

We are searching for discriminative algorithms. And when this becomes difficult we transform the data in such a way that the same algorithm becomes discriminative. Think about Support Vector Machines and kernel methods with non-linear data.
According to the General Data Protection Regulation, sensitive data includes:

    - personal data revealing racial or ethnic origin,
    - political opinions,
    - religious or philosophical beliefs,
    - or trade-union membership,
    - the processing of genetic data, biometric data for the purpose of uniquely 
    identifying a natural person,data concerning health or data concerning a natural 
    person’s sex life or sexual orientation…

 

In the third paragraph of Article 11, they specifically address discrimination from profiling of  sensitive data.

But there are cases in which it would be possible to get to the same conclusion by analysing other types of data. For example, if a certain geographic region has a high number of low income or minority residents, an algorithm utilizing geographic data can determine loan eligibility based on race and income, due to analogy or what we data scientists define as common patterns.

In clinical data analysis we might have exactly the same scenario. Also in politics and social media (by analyzing how a user is connected and to who, to predict his or her interests and opinions or religious views). There was a research paper in which an algorithm could even guess the girlfriend/boyfriend of a Facebook user just by analysing his or her ego-network that is how his/her friends were connected.

So what would be the solution to avoid discrimination with data analysis? De-correlate data? Or use only data that are not correlated to sensitive information? Who defines the correlation measure? Is Pearson 0.3 a good measure? This starts to sound a bit ridiculous.

As data grows, detecting correlated (or uncorrelated) variables becomes extremely difficult if not impossible. This is actually still an open research problem.

If correlation with sensitive data is the enemy here, one solution would be to operate only on uncorrelated data. Which can result poor in terms of informative power and useless to perform predictions.

 

Whoever wrote this regulation should be aware of the fact that Correlation is not causation and actually it doesn’t even imply it!

Maybe they were worried to conserve confidentiality and protect one’s privacy by predicting causality.

But with regression or classification or machine learning in general I cannot say if race, ethnicity and political views of a person will cause that person to be unreliable in paying back a loan. That would mean predicting causality. Which is not correlation.

 

I have the impression that politicians and apparently philosophers are trying to regulate something that just cannot be regulated, 
a bit like the Internet or any other massively adopted technology that at some point of human history became fundamental part of everyday life and it is impossible to limit or prevent.
I expect that real data scientists supported those philosophers, making sure they understand what is already happening, what is feasible and what will never be.
I also see an analogy with the field of software security some years ago, in which lawyers and politicians tried to regulate transmissions of bits and bytes to mitigate the problem of copyright infringement with written rules and regulations that found their interpretation in different countries of EU.
What happened? 
Hackers tried to circumvent those restrictions in technology. And to download movies and music for free, we got Tor anonymizer networks, proxies, and decentralized protocols to share information, with or without encrypted connections.

 

Having operated in software security for more than 5 years, I expect that similar figures that we have already seen would rise, maybe the best name would be data hijackers that would try to circumvent those restrictions as much as it already happened for the Internet in general.
Those who are trying to stop the storm of data coming from the IoT are getting my attention. Because this is going to be really really challenging.

I am just thinking about a few of these circumventions by Data Hijackers.

For instance, due to the ease of allocating computing resources in the cloud and crunching data of any kind, a black market of data science could grow, in which no model would need to be explained.

Even in let’s say legally recognized analytic procedures, ? some variables cannot be used because they belong to the black list of sensitive variables?

Fine! I’m gonna search for collinear variables or groups of variables that are not in such lists and still get my prediction pretty accurately.

So, folks, do you think this is going to be difficult with big data?

Not at all. We are doing this already.

