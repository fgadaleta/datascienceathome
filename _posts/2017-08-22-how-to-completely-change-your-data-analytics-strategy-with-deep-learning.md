---
title: Completely change your data analytics strategy with deep learning
layout: post
summary: "I am recording this episode from South Africa, exactly in Cape Town, as we are currently participating to the Barclays accelerator powered by Techstars, putting our AI expertise to the test in the complex financial environments of corporations like Barclays and their affiliates. "
comments: true
tags:
- NLP
- AI
- deeplearning
---

> #### This post has been published as podcast episode on Data Science at Home. You can listen [here](https://www.podbean.com/media/share/pb-rj4dn-6ed672)

<hr>


A lot has happened since the last episode. I left corporate industry and joined [Abe](http://abe.ai) as Chief Data Officer. Abe is a startup from Florida building artificial intelligence solutions for personal finance, supporting both banks and people with their money, via a conversational and natural experience through the many channels they are used to, such as Facebook messenger, mobile app, SMS, but also smart speakers like Google home, and Amazon Alexa.
I am recording this episode from South Africa, exactly in Cape Town, as we are currently participating to the Barclays accelerator powered by Techstars, putting our AI expertise to the test in the complex financial environments of corporations like Barclays and their affiliates.  I am personally having a lot of fun, tackling really challenging problems in financial analytics and advanced machine learning on one side. But also more AI related problems typically in the field of natural language processing or NLP. Which is exactly what I planned for this episode.

Over the past few years, neural networks have re-emerged as powerful machine-learning models, reaching state-of-the-art results in several fields like image recognition and speech processing. More recently, neural network models started to be applied also to textual data in order to deal with natural language, also with promising results.

For a long time, core NLP techniques have been dominated by machine-learning approaches that are rather based on statistics and function optimisation. I am referring to  linear models such as support vector machines (SVM) or regression, trained over high dimensional data and sparse feature vectors.
In contrast, neural networks are nonlinear objects and since there are not so many linearities in complex languages like those spoken or written by humans,  this explains why neural networks are showing such promising results. With this said, a lot needs to be done to - let’s say - crack the problem of natural language modeling, but these are definitely exciting times for AI.

Every time I mention neural network modeling, the most common question I get is about the number of architectures currently in the literature and the fragmentation that so many architectures are creating. I’d like to clarify this point.
Despite the number of different neural network architectures, there are basically two major families of models:  **Feed-forward networks** and **Recurrent/Recursive networks**

* Feed-forward networks include networks with fully connected layers, such as the multi-layer perceptron, as well as networks with convolutional and pooling layers

* Recurrent and recursive networks can work with sequences and trees respectively. Recurrent networks (Elman, 1990) are designed to model sequences - of characters, words, numeric sequences, etc - while recursive networks (Goller & Kuchler, 1996) are generalizations of recurrent networks that can handle trees (something like dependency graphs for text parsing and language modeling).


Both networks can contain convolutional and pooling layers. These are matrix operations that make the network robust specifically against scaling, transforming, resizing, and therefore being more appropriate for images and pixels. It turns out that convolutional and pooling architectures are showing promising results also on characters, words and tasks such as  document classification. As a matter of fact all of the networks are basically classifiers, of course each one with with different strengths and properties that make them more suitable for text, sound, or mixed data.

Without any doubt, the most important finding with deep learning for NLP has been the concept of **word embedding**.
So far words have been represented in very high dimensional spaces, like *one-hot encoding* for instance or *bag-of-words*, generating very sparse feature vectors and definitely increasing the dimensionality of the problem, leading to computational complexity and shortage of memory.

The key idea behind the neural approach is that each word in a vocabulary can be represented with a dense vector of real numbers, so that *similar* words are forced to have similar vectors. This is usually done by training the network on large textual datasets in a skip-gram fashion in which the network is trained to predict each word given a number of previous words (usually referred to as *the context*). This can be done just by scanning or reading digital books millions of times, and after some hours of computation, words that are similar will have similar numeric vectors. Of course word similarity is hard to define and is usually task-dependent.
What does similar mean? Are two words similar because they have similar characters, or similar length, or similar meaning? The most common hypothesis in this case is the *distributional hypothesis* : words are similar if they appear in similar contexts.
No matter what the meaning of similarity is, word embedding reduces the dimensionality of the problem and the memory footprint of any neural model, especially those with many layers, also called *deep networks*.

With this said, it is important to mention the fact that neural networks can also fail in many different ways and diverse scenarios

## Causes of failures of deep learning
Here are probably the most common causes of failure of deep learning

* Function optimization can be made difficult due to geometric reasons such as other than local minima and saddle points
* Condition number and flatness
* Using bigger/deeper networks. Most of practitioners are prone to such a common mistake of increasing the depth of a network, which in turn increases the number of parameters and makes the network more prone to overfitting. Deeper network not always help

### Some remedies

* Using prior knowledge can constrain the problem enough to reduce the degrees of freedom of the network, still maintaining the number of parameters relatively high
* Convolution can improve the geometry of the sample
* Convergence can be perfomed by *other than gradient*  rules that can perform better than the off-the-shelf gradient descent
* Decomposing the problem and adding supervision can also improve geometry. Splitting a deep network in a number of intermediate steps to train separately can constrain the learning mechanism further and improve accuracy overall.

### Understanding the limitations
While deep learning is a great technique to learn structures from data, understanding its limitations may lead to better algorithms and/or better theoretical guarantees. A paper that better explores the ways deep learning can fail is “Failures of Deep Learning” on [arxiv](https://arxiv.org/abs/1703.07950)

## Data availability
As a matter of fact, data is expensive. Crawling data and pre-training deep learning models with less related but public datasets can be effective in some cases.
Academic datasets are usually perfectly balanced. In the real world, however, datasets are messy, unbalanced and incomplete. As an example, the MNIST image dataset contains an equal number of samples per digit which is hardly the case in real world image classification problems; in finance, very few individuals are at risk of overdraft with respect to the entire population, and fortunately very few of them perform fraudolent activities of money laundering and illegal credit card payments. Still artificial intelligence models should be capable of learning from those very few examples and profiles. Scenarios like the one described do not change in domains like healthcare, where fortunately very few individuals are affected by disorders or diseases with respect to the rest of the population. This in turn might give a hard time to a deep learning medical image classifier.

A consequence of the challenging problems of the type just described, is represented by models that make mistakes in the form of false positives (or false alarms) and false negatives (missed signals). In finance this might mean missing fraudulent activities or stopping payments for no reason. Both the cases are expensive for a bank and definitely annoying for the end user.

These are the real problems that researchers have to deal with complex models like deep learning.

My take home message however is about being aware that complexity of fancy models can be detrimental, and not the silver bullet that many claim. Even in the realm of deep learning, *simplicity is the ultimate sophistication*.
