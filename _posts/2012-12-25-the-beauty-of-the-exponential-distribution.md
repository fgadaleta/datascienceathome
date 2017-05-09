---
layout: post
title: the beauty of the exponential distribution
comments: true
tags: [breaking, distribution, exponential, lambda, quality, risk, rupture, statistics]
---

### Problem description

<img src='/img/img_posts/exponential_distribution.png' />

Things break. Well, let me put it more softly: everything has a finite
lifetime. 

Good thing is that mathematical statistics can help making light about that amount of time. 

A problem I was dealing with recently made me think about how wonderful the exponential distribution is to model things that break. 

Given the lifetime of an object by a random variable $$X \sim F$$ where $$F$$ is an unknown cumulative distribution function and $$ f$$ represents its density function, we can define the risk function - that gives
the intensity of the rupture - as $$\frac{f(t)}{1-F(t)}=\lambda(t)$$. 

---

> What a data scientist really wants to know
> is the probability that something breaks after a time $$ t$$

---


Basically, what this ratio says 

$$ P(X \in (t,t+dt)|X>t) = \frac{P(X \in (t+dt), X>t)}{P(X>t)}=\frac{P(X \in (t,t+dt))}{1-F(t)}$$ 

The formula above can be approximated with $$\frac{f(t) dt}{1-F(t)} = \lambda(t) dt$$, that is the conditional density that something will break right after time $$ t$$. 

And now comes the trick. 

Imagine $$ X$$ is a random variable from an exponential distribution (its density function is given by
$$ f(x) = \lambda e^{(- \lambda x)}$$, $$ x \ge 0$$), then 

$$ \lambda(t) = \frac{f(t)}{1-F(t)} $$ and 
$$ \frac {\lambda e^{(- \lambda t)}} {1-1+ e^{(- \lambda t)}}$$, 

that is the parameter of the exponential distribution indeed. This parameter is usually provided by the
vendor of the object that is going to break.  It can be a number or even an
equation with some other parameters. The problem is how to determine $$ F $$ from parameter $$ \lambda $$. 

And there we go: 

$$ \lambda (s) = \frac{f(s)}{1- F(s)} = \frac{F'(s)}{1-F(s)}= - \frac{d}{ds} log(1-F(s)), s=2$$

Integrating both members of the equation above, we get 

$$ \int_0^t \lambda (s) ds = - log(1-F(t)) + log(1-F(0)) = s=2$$ $$ -log(1-F(t)), s=1$$, $$ 1-F(t) = e^{(\int_0^t \lambda(s) ds)}, s=2$$ 

Therefore $$ F(t) = 1 - e^{( \int_0^t \lambda(s) ds)}, s=2$$ et voila'. 


## Conclusion

By knowing parameter $$ \lambda $$ it is possible to calculate the cumulative
distribution function and therefore the density function (by its derivative)
of the random variable that indicates the lifetime of the object we want to
estimate. 

Merry Christmas (oo)

