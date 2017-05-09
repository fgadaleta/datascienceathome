---
layout: post
title: Hypothesis testing explained
comments: true
tags: [hypothesis testing, pvalue, statistics]
---

This post is dedicated to all those who still believes that _R in a nutshell_ is a
book for learning statistics... Let's get started with the easiest question.

### What is a hypothesis?

In statistics, having a hypothesis means that we believe that the value of a parameter, 
for instance the mean or the variance of a distribution is close to a certain number. 
As all statements it can be correct or completely wrong. 
Data will tell us  what seems to be correctly explained.
In order to overcome the trickiness of the concept let's define some
terminology that might be helpful in the next paragraphs. Before the actual
analysis, scientists usually formulate some questions they would like to
answer. Those questions are technically referred to as _hypotheses_. Given the
null hypothesis $$H_0$$, the alternative hypothesis $$H_1$$ and the
sample $$ (x_1, x_2, \dots x_n)$$, the _rejection region_ (also called
**critical region**) is defined as the region C such that if $$ H_0$$ is
accepted, $$ (x_1, x_2, \dots x_n) \notin C $$. Similarly if $$ H_0$$ is
rejected, the data do belong to $$ C $$. 

Probably the most classical way to
explain hypothesis testing is by referring to the gaussian distribution with
both mean and variance known. Let me oversimplify the problem of cancer
attacked with statistical analysis tools. 

Imagine that there are some reasons to believe that gene RSPC is
responsible of a type of cancer. Moreover, doctors have samples of patients
who are affected by cancer (control). The control sample has a mean value for
gene RSPC, $$ \mu_{RSPC}$$. The idea behind hypothesis testing is that if
another group of patients has a mean value that is close enough to $$
\mu_{RSPC} $$, the hypothesis $$ H_0: \mu = \mu_{RSPC} $$ will be accepted and
the group will be labeled as _affected_. Contrarily, if the mean value is not
close enough to $$ \mu_{RSPC} $$ then $$ H_1: \mu \neq \mu_{RSPC} $$ should
be accepted instead and the group will be labeled as _not at risk_. In terms
of the critical region, the aforementioned hypotheses are saying that if the
sample under investigation belongs to the critical region, we better reject
$$H_0$$. 

No need to be a genius to conclude that if the sample does not
belong to the critical region, we have a good reason to accept $$ H_0$$,
instead. Fine! 

Let's define the critical region and we are done. Under the
assumption of gaussian distribution with known variance $$ \sigma $$ the
critical region 
$$ C = {(x_1, x_2, \dots x_n): | \hat{X} - \mu_{RSPC} | > c} $$, 
where $$ \hat{X}$$ is an estimator of the mean (sampled mean). What
is $$ c $$ then? $$ c $$ indicates how far from the given mean we accept
the estimated mean can go and still consider the test acceptable or
_significant_. That's why it depends on two other concepts I'm introducing
now: the **type I error** and the **significance level** $$ \alpha $$. The
former represents the error we could make by rejecting $$ H_0$$ when it is
true. The latter is an upper bound of the probability of such an error. The
probability to reject, erroneously, $$ H_0$$ should be kept under control
and should be lower than $$\alpha$$. Therefore, $$ \alpha = P(type I
error) = P_{H_0}( |\hat{X} - \mu_{RSPC}| > c)$$ 

Am I annoying if I say that again? $$ \alpha $$ is the probability that the given sample belongs to the
critical region (and $$ H_0$$ should be rejected for that) but imagine that
a prophet told us in a whisper that $$ H_0$$ is true and must be accepted
instead (that's what $$ P_{H_0}$$ stands for). Does it sound enough like an
error? That's what statisticians call **type I error**. Under the assumption
of normal distribution, the test statistic measure $$ \frac{\hat{X}-\mu_{0}}{\frac{\sigma }{\sqrt{n}}} \sim Z$$. 
Therefore the probability
we are looking for is $$ \alpha = P(|Z| > \frac{c \sqrt{n}}{\sigma}) =
2P(Z>\frac{c\sqrt{n}}{\sigma}) $$ and in conclusion $$ P(Z >
\frac{c\sqrt{n}}{\sigma}) = \frac{\alpha}{2}$$ 

From the definition of the cumulative distribution function and the area under the Normal Curve $$P(Z >
z_{\frac{\alpha}{2} }) = \frac{\alpha}{2}$$.  
Therefore, $$ \frac{c \sqrt{n}}{\sigma} = z_{\frac{\alpha}{2}}$$ and $$ c = z_{\frac{\alpha}{2} }
\frac{\sigma}{\sqrt{n}}$$ 

Almost there. A test with significance $$ \alpha $$
should reject $$ H_0$$ if $$ |\frac{\hat{X} - \mu_{RSPC}}{\frac{
\sigma}{\sqrt{n}} } | > z_{\frac{\alpha}{2}}$$ 

Whenever the analyst feels the
presence of higher reliability about the truth of her hypotheses, she can
transmit her feelings to the significance level $$ \alpha $$ and relax it
too. In fact, a much stricter hypothesis testing would be conducted with a
very small $\alpha $$. This is translated into being less tolerant about
the probability of the _type I error_. 

The beauty of mathematical statistics
consists in the capability of explaining the same concepts in so many
different ways. Very often, academic papers and research studies in general
exploit the concept of **p-value**. Once the statistic measure is computed
from the data (in the example above it is $$ |\frac{\hat{X} -
\mu_{RSPC}}{\frac{ \sigma}{\sqrt{n}} } |$$) we might be interested in evaluating
the probability that a random sample from the standard normal distribution is
greater than our statistic measure. That probability is what they call the _p-
value_. If that probability is greater than the statistic measure and that
happens a number of times, then $$ H_0$$ should be accepted. 

How many times? $$ \alpha $$, of course! 

### Notes 

The simplification about cancer above is just ridiculous, I know. I've also read quite a number of
papers in which they claim to govern the complexity of some aspects of (some
types of) cancer with hypothesis testing, which I also find ridiculous.

