---
layout: post
title: there is no mutual information without entropy
comments: true
tags: [entropy, mutual-information, theory]
---

<center>
<img src="/img/img_posts/entropy.jpg" />
</center>

<center>
Courtesy of nathanwatkinsdesign.com
</center>

---
The concept of _entropy_ is itself confusing and, so far, with high entropy.
When I associate it with the concept of mutual information, its entropy
decreases. Alright, I got my chance to confuse the reader and that was
actually fun. 


_Entropy_ is one of the most confusing concepts that has been
borrowed by computer scientists from physicists studying thermodynamics. 
Just ignore for the next two lines what _entropy_ should be. Think about it as
something that measures something else. 

Now, imagine a bunch of molecules in a glass at time $$ t_0 $$, temperature $$ T_0 $$ and pressure $$ P_0 $$. The entropy of that system would be $$H_0 $$. 
As the temperature decreases, the molecules slow down
and tend to stabilise to a fixed position. As time goes, the entropy of the
system decreases and the information, as the _"certainty"_ of the exact
position of each molecule increases. This can be extended to an extreme case
in which the temperature is so low (absolute zero) that all the molecules
remain in a position that we can measure exactly. In that case we are not only
100% sure that the measured position is the real one, but also that the system
cannot come into a different configuration. The entropy of such a system is at
its minimum. No uncertainty. No alternative configurations.

> As the temperature decreases, the molecules slow down and tend to stabilise to a fixed position. That's when entropy is at its minimum

Since we're not doing physics here, let's go back to planet earth and do some information theory.
The concept of _entropy_ is somehow linked to the **amount of uncertainty** of a system and to the amount of _information_ that is present in a random signal. 
The entropy at a source that emits a signal $$x$$ with probability $$p(x)$$ is given by
$$ H(X) = p(x) log( \frac{1} {p(x)} ) $$ 

If the message can be represented by an alphabet of $$ M $$  symbols,  
$$ X = {x_i}, i = 1 \dots M $$ 
and the source emits  $$ x_n $$ symbols with $$ 0 \lt; n \lt; \infty $$, the entropy at
the source is 
$$ H(X) = \sum_{i}^{M} p_i log(\frac{1}{p_i}) $$. 
Usually, the term $$ log \frac{1}{p_i} $$ is referred to as $$ I(X) $$ and called
**information**. 

A quite simple explanation of this is that a very frequent symbol (for which $$ p_i $$ would be high) contains little information; a rare symbol, on the other hand, contains a high amount of information about the overall message. 
It makes perfect sense to me. Or does it? 

With this said, let's jump to the mutual information between two variables $$ I(X;Y) $$. 

This quantity measures the mutual dependence between $$ X$$ and $$ Y$$. 

It is given by

$$ I(X;Y) = H(X) - H(X|Y)= \sum_{y}\sum_{x}p(x,y) log(\frac{p(x,y)}{p(x)p(y)}) $$, 
which basically translates into "how much information from knowing $$Y$$, reduces the uncertainty about $$X$$?" 

In fact, if $$X $$ and $$Y $$ are independent, then $$ p(x,y) = p(x)p(y) $$ and $$I(X;Y) = 0 $$. This too makes perfect sense to me. There are some properties that make the
link between mutual information and entropy even stronger. I will list a few:

1\. $$H(X) = I(X;X)$$, means that the mutual information between $$X $$ and itself
is its entropy. Once $$X$$ is known, the amount of uncertainty about $$X$$ itself
is indeed its entropy 

2\. with $$H(X|X) = 0 $$, one means that the amount of uncertainty about 
$$X $$, that remains after $$X$$ is known is $$ 0 $$. 

3\. More generally, 
$$I(X|X) \ge I(X;Y)$$, 
which means that a variable contains at least as much information as the one provided 
by any other variable.

4\. 
Finally, $$ H(X) \ge H(X|Y) $$, which means that uncertainty decreases as other variables are known (namely, as the system goes towards a fixed certain state). 

> One elegant interpretation of entropy in statistics is the Kullback-Leibler divergence

Let's revisit these concepts in statistics now. 
One of the most explicative interpretations of mutual information is the one that recalls the [Kullback-Leibler](http://en.wikipedia.org/wiki/Kullback%E2%80%93Leibler_divergence "Kullback-Leibler divergence" ) distance between distributions. 

It represents mutual information as 

$$ I(X;Y) = D_{KL} (p(x,y) || p(x) p(y)) $$

that I find elegant and amazing at the same time. Let me just add this reconstruction: 

$$ p(x|y) = \frac{p(x,y)} {p(y)}, p(x,y) = p(x|y) p(y) $$ 

$$ I(X;Y) = \sum_{y} p(y) \sum_{x} p(x|y) log \frac{p(x|y)p(y)}{p(x)p(y)} = \sum_y p(y) D_KL (p(x|y) || p(x) ) = E_y[D_{KL}(p(x|y) || p(x)] $$ 

that means the more 
$$ p(x|y) $$ 
differs from 
$$ p(x) $$, 
the higher the amount of "information gain". 

Cool uh?
