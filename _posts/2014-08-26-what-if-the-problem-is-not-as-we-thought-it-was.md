---
layout: post
title: What if the problem is not as we thought it was
comments: true
tags: [analysis, biology, genetics, modeling, statistics]
---

At the end of GAW19, a very interesting workshop about Genetic Analysis, held
in Vienna last week, I find it necessary to take a big breath and draw some
conclusion. Or maybe start a new way of thinking about *The problem*. Genetic
analysis is not an easy task to solve. We all know that. When we try to put it
in mathematical terms, the problem is likely to be ill-posed, being the number
of unknowns larger than the known variables. When we do it in statistical
terms, there is too much uncertainty. Are we doomed to leave such problems
unsolved, acknowledging that we spent billions and we actually lost that
money? Not so fast. Research works like that. 

No substantial discovery is made on day-to-day basis. 
But when it happens it is big (ignoring the micro steps
of the $$k_{t}$$ paper that improves on the $$k_{t-1}$$, that in turns improves on the
$$k_{t-2}$$, and so forth in a pretty indefinitely long sequence of publications
that nobody read but that is cool to refer to). 

The observation of a
researcher I know, [What if the genome does not explain
enough?](http://cancersystemsbiology.blogspot.co.at/2010/07/what-if-genome-
does-not-explain-enough.html "What if the genome does not explain enough?" )
was raised only four years ago. I believe it is still a good one that made me
think deeply about the subject and realise that, maybe, the common feeling
about research in genetics has not changed much. This is just a feeling of
course, which I hope could be disproved. Let me refer to the problem of
inferring gene regulatory networks. So much science has been called to the
rescue and so many researchers (mainly statisticians) have been hired to take
care of such a challenge. The most common tools that researchers (I ashamedly
include myself here) are considering since ages are regression (in all its
flavours, linear, non-linear, penalised, etc.), Principal Component Analysis
or PCA (in all its flavours, independent, randomised, kernel, etc.),
statistical correlation which usually leads to clustering highly correlated
genetic compounds within the same group. 

Is this solving the issue? Not
really. As Gordon Webster summarises in a beautiful and diplomatic way on his
blog, [the digital biologist](http://www.digitalbiologist.com/2012/05
/biologists-flirt-with-models.html "the digital biologist" ), 

> Looking back over almost a decade since the first working draft of the human genome was
completed […] I think it is fair to say that the impact has not been on
anything like the scale that was initially anticipated, largely as a result of
having underestimated how difficult it is to translate such a large and
complex body of data into real knowledge.”

What statistics is certainly doing
is giving researchers a grip on the problem. Interpreting the regression
coefficients of some genes as handlers to manipulate a limited number of
genetic compounds (statistically) associated to the trait under investigation
is a relief indeed. However, considering such a result an **oracle** that
should be undeniably used for subsequent analyses is equivalent to accepting
the idea that dipping one foot into fire and the head into ice leads, on
average, to a comfortable temperature. 

Speaking to a medical doctor I met at
GAW, who is genuinely interested in exploring the new insights of
computational biologists, we agreed on what we both see as a trend in our
community: when a model works 3 times out of 100, improving on that other
model working only 0.2 times out of 3000 (and this is rather optimistic), we
tend to claim that we're done. The best model is almost considered a gold
standard, it gets a bunch of citations and becomes _The Way_ of solving things
in the future. What exactly is happening is that by doing so we are accepting
the average of the average of the average result and we are pretty much happy
with that. 

### Statistics is not biology 

How could such an abstraction be
interpreted as a real thing? Going back to the question of _"What if the
genome does not explain enough?"_ I do agree that indeed it might not.
Actually I am pretty sure it doesn't. But, once the majority will figure out
that this might be the case, the real question will be _"What if statistics
does not explain it at all?"_ 

My conclusion wants to be provocative, of
course. But is there anybody out there who **truly** believes that complex
genetic traits are merely a statistical problem in which a t-test or anova
would provide a solution? Statistics, as I see it, is just a wonderful
abstraction that gives us a comfortable point of view on complexity. If we do
not accept the fact that it is just a starting point, _not an oracle_, then
yes!, we are doomed to leave our problems unsolved. 

Happy research! 

(oo) Piggy


