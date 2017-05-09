---
layout: post
title: Stability of stochastic gradient descent
tags: [google, gradient-descent, loss, minimization, optimization, sgd, stability, stochastic]
comments: true
type: post
---

A paper that, in my opinion, will be more influential than the garbage
constantly published on many paid journals, is "Train faster, generalize
better: Stability of stochastic gradient descent", written by [Moritz
Hardt](http://mrtz.org) at Google. 

The authors published it on
[Arxiv](http://arxiv.org/pdf/1509.01240v1.pdf), from where it can be
downloaded for free. In the aforementioned paper, the stability of stochastic
gradient descent, SGD, is formally proved for convex, non-convex L-Lipschitz
loss functions. 
That basically means that SGD is guaranteed to be stable under
certain assumptions. People at Google have the tendency to be practical and
avoid the nonsense of academia as much as they can. The assumptions the
authors claim in the paper are indeed more than realistic. 

### What is Stochastic Gradient Descent

Stochastic gradient descent is a method that minimizes the loss function of a model by repeatedly
computing its gradient on a single training example, or a batch of few
examples. As a result of the minimization problem, a set of parameters is
updated at each iteration. The difference with the classic gradient descent
algorithm is exactly in how much samples are considered at each iteration. All
of them for Gradient descent and just one or a few for SGD.
 
As a consequence, *SGD is scalable*, robust, and performs quite well across many different domains
with smooth, convex loss functions but also with complex non-convex ones. The
trick is in training the model on very small subsets of the data. 
What the authors found is that any model trained with SGD will get a small
generalization error in a reasonable amount of time. 
In practice, with a sufficient number of iterations that is linear in the number of observations
(the dataset), SGD contains the error, stays stable, and prevents overfitting
even without any regularization term. 

**Regularization** (eg. *L1-norm*) is usually added to the loss function to minimize in order to reduce the number of
covariates in a regression method. This approach deals with high dimensional
data and prevents overfitting. 

The reason for which SGD prevents overfitting by design is, once again, given by 
the limited subset of data points used to train the model. 
If SGD overfits the training data in a number of iterations,
it is still guaranteed to generalize because that training subset is so small
that overfitting would not be critical. Of course, those who would like a formal
proof of what has been claimed thus far, need to read the paper, which might
be a bit challenging but definitely interesting. 



