---
layout: episode
category: podcast
title: Machines that learn like humans
date: 2017-03-28
keywords: [machine learning, data science, analytics, google]
producer: worldofpiggy.com
explicit: No
block: not available
duration: "42:08"
length: 13400000
media: https://s3.amazonaws.com/dshpodcast/media/datascience_episode_18_lifelong_machine_learning.mp3
excerpt: Artificial Intelligence allow machines to learn patterns from data. The way humans learn however is different and more efficient. With Lifelong Machine Learning, machines can learn the way human beings do, faster, and more efficiently
comments: true
---


<img src="https://s3.amazonaws.com/dshpodcast/media/cover.jpg" />

<strong>Francesco:</strong>
Hi Brett, thanks for being here. How are you? Can you give a brief introduction of who you are and what do you do?

<strong>Brett:</strong>
Thanks Francesco! Hello, everyone, my name is Brett Zhiyuan Chen. My background lies in Machine Learning,
Natural Language Processing, and Data Mining. I obtained my Ph.D. from University of Illinois at Chicago.
My advisor is Professor Bing Liu. My Ph.D. thesis is “Lifelong Machine Learning for Topic Modeling and Classification.”
I have published more than 15 full research papers in premier conferences. Together with Professor Bing Liu, I have given
three tutorials in Artificial Intelligence, Data Mining and Natural Language Processing conferences. I am currently a
software engineer at Google, working on applying Machine Learning to Google products.

<strong>Francesco:</strong>
I have been reading your book during the Christmas break and I must admit there is a number of interesting points you
and prof. Bing make.
I was intrigued by some chapters in the book for instance chap 2. And definitely chapter 5.


### Outline of the book
- Chap 2: how to make ML more intelligent and closer to human learning
- Chap 4: unsupervised LML focusing on lifelong information extraction and lifelong relaxation labeling
- Chap 5: Never Ending Language Learner or NELL
- Chap 6: Lifelong Reinforcement Learning
- Chap 7: future directions

In the book you start mentioning the current ML paradigm. The current dominant paradigm for machine learning is isolated
learning, namely a ML algorithm is trained on a given dataset and deployed somewhere else, where eventually data is assumed
to have the same distribution of the training data... otherwise it might not work.
Isolated learning, however, does not consider any additional information or knowledge that might have been learned already
previously. It’s basically a memoryless approach, but it is the most widely adopted approach to machine learning currently.
Why is that?

<strong>Brett:</strong>
That’s a wonderful question. In my opinion, there are three main reasons:
First, isolated learning is a problem that fits the academic research very well. It assumes that the training data and the
testing data has the same distribution. The setting is more focused and easier to evaluate, and therefore, it has received a
lot of attention. But in recent years, researchers found that in reality, the test data is not always sharing the exactly
same distribution with the training data. That is where lifelong machine learning comes into the picture.
Second, there are some related learning paradigms that are more flexible than isolated learning, e.g., transfer learning
and multi-task learning. Transfer learning tries to transfer knowledge from a source domain to a target domain.
Multi-task learning optimizes the objective function across all tasks. They are closer to lifelong machine learning in the
sense of knowledge transfer.
Last but not the least, lifelong machine learning was hard to do due to lack of suitable datasets. For a lifelong machine
learning system to work, the system has to learn from many diverse datasets. The recent evolution of big data provides a
large volume of diverse data for researchers to study lifelong machine learning.

<strong>Francesco:</strong>
So these are really great times to put lifelong machine learning to the test...
Going back to isolated learning, there are cases in which it can be impossible to enumerate all possible scenarios that
represent a phenomenon. That’s why the need for a large dataset can be seen as a drawback. What do you think might be a
benefit of isolated learning?

<strong>Brett:</strong>
Interesting question. The main problem is how we decide the completeness of the training data. For simple tasks, such as
handwritten digit recognition, it is not difficult to obtain a large volume of training data that covers most scenarios.
As a result, isolated learning can achieve very high accuracy on such simple tasks.
On the contrary, for more sophisticated tasks, obtaining the “complete” training data is very hard, if not impossible.
Let’s take sentiment classification as an example. Sentiment classification tries to classify a sentence or document into
positive, neutral or negative polarity. The task is challenging because there are so many different ways to praise or
criticize things. People can have different opinions on almost everything in the world. Let alone the new expressions/phrases
coming out of social media every single day. In this sense, it is impossible to collect the perfect dataset that covers
everything.

Which leads us to a more philosophical question. We believe that the way humans learn is dramatically different from how
computers learn. Computers need a lot of data. Humans usually learn from much less “data”. What do you think is more
powerful and why?

<strong>Brett:</strong>
I think the reason that computers need a lot of data is mainly because most systems/models are built from scratch.
They are purely constructed based on the data provided. Computers do not really “learn” now. What it does is to generalize
the given data, and perform predictions based on the generalization. The resulting knowledge is similar but also different
from human knowledge because it is often not transferrable. It is obtained from *that* data for *that* task, and thus not
useful to other tasks.

Human knowledge, on the other hand, is learnt from years of experience, and summarized using things that can be easily
transferred, such as languages or symbols. That’s why humans don’t see many things that are completely new, and only need
information or data to learn the new aspects.
That’s to say, we believe that without the knowledge accumulation and continuous learning as proposed in lifelong machine
learning, computers will never be truly intelligent.

<strong>Francesco:</strong>
This is a really strong statement, I agree. Maybe some researchers out there will agree less :)
According to the brief history of lifelong machine learning proposed in the beginning of the book, it seems that concepts
like the one you describe have been introduced back in 1995. Why Lifelong Machine Learning never took off?

<strong>Brett:</strong>
I am glad you asked this question. Many others asked me this question before. Professor Bing Liu and I have been thinking
and discussing it when writing the book. In the book, we have a section covering the history of lifelong machine learning.
I believe there are several main reasons that research in the area has not been extensive.
The machine learning research for the past 20 years has mainly focused on statistical and algorithmic approaches.
LML typically needs a systems approach that combines multiple components and learning algorithms.
Much of the past machine learning research and applications focused on supervised learning using structured data, which are
not easy for LML because there is little to be shared across tasks and domains. For example, the knowledge learned from a
supervised learning system on a loan application is hard to be used in a health or education application because they do
not have much in common.
Many effective machine learning methods such as SVM and deep learning cannot easily use prior knowledge even if such knowledge
exists. These classifiers are usually black boxes and hard to decompose or interpret. They are generally more accurate with
more training data.
Related areas such as transfer learning and multi-task learning were popular partly because they typically need only two and
just a few similar tasks and datasets, and do not require retention of explicit knowledge. That’s an easier setting to conduct.
Last not but the least, as I mentioned before, the lack of big, diverse data also held LML back.
I personally believe this is the right time to study lifelong machine learning. The main intent in this book is to introduce
LML and also encourage people to study, adopt and advance this area.

The major goals of Lifelong Machine Learning are very challenging. For instance, choosing which knowledge to retain for a
certain task, or how to use learned knowledge and maintain the so-called knowledge base are currently open problems across
ML in general. How does/would LML solve them?

<strong>Brett:</strong>
So far, the research in LML is still in its infancy. So there is no magic solution here. It is currently still case by case,
and largely rely on the tasks and specific algorithms. To give you a taste how existing LML systems solve this problem, let me
briefly talk about our work on lifelong topic modeling, which was published in conferences ICML 2014 and KDD 2014.
Topic modeling is a research problem that attempts to automatically discover a set of semantic topics from a collections of
text documents. For example, from some News articles, the model may uncover the topics “Politics”, with some relevant words
such as politician, government, congress and so on. Lifelong topic modeling aims at improving topic coherence by mining and
retaining knowledge from previous topic modeling tasks.

In our particular work, the knowledge is formed as must-link and cannot-link. A must-link states that two terms (or words)
should belong to the same topic, e.g., price and cost. A cannot-link indicates that two terms should not be in the same topic,
e.g., price and picture. Here, the knowledge is automatically mined. We try to retain all the knowledge that satisfies the
potential usefulness criteria. But usefulness is not equal to correctness when it comes to a new task. For example, word light
may mean “something that makes things visible” and thus forms must-links such as {light, luminance}. But in a new task, word
light may be dominantly used as the meaning “of little weight”, which has nothing to do with luminance. To address this, we
used frequent itemset mining and pointwise mutual information to approximate the semantic correlation using the new task data.
The knowledge is then selected based on how they correlate to this approximation.

<strong>Francesco:</strong>
frequent itemset mining is the same used for market basket analysis?

<strong>Brett:</strong>
Yes. In summary, there is no magic solution. This is an interesting open question for research.

<strong>Francesco:</strong>
You can use this podcast to make a call if you wish :)
I now do a lot of deep learning work as other followers of Data Science at Home, and I have seen many approaches that are
analogous to LML. I am referring to
attention-based models that indeed are helpful in focusing on certain aspects of the data to make a prediction or
knowledge transfer by which a neural network can perform predictions in a domain that is different from the one where it
has been trained. Does LML embrace such concepts, or revisit them or change them completely?

<strong>Brett:</strong>
This is a great question. The idea of attention mechanisms in deep learning is very interesting. It is motivated by human
visual attention. It comes down to being able to focus on a certain region of an image with “high resolution” while perceiving
the surrounding image in “low resolution”, and then adjusting the focal point over time. It aligns with the idea in LML that
given a new task, we want to focus on this task with “high resolution”. But we do not ignore the previous tasks. Instead, the
previous tasks are treated in “low resolution”, meaning that the knowledge is abstracted from them and applied to the new task.

In terms of your second point, knowledge transfer is one of the key components in LML. In the book, we also covered some recent
deep learning works with knowledge transfer. Most of the works are in transfer learning, which involves two domains: a source
domain and a target domain. The source domain normally has a large amount of labeled training data while the target domain has
little or no labeled training data. The goal of transfer learning is to use the labeled data in the source domain to help
learning in the target domain. LML, instead, deals with a large number of tasks in a sequence and explicitly retain knowledge.
The early works of LML used neural networks, where a global network is learnt across multiple tasks. More details can be found
in the book.

I believe deep learning can be even more powerful when incorporating LML. The knowledge retained and accumulated from previous
tasks can help deep learning learn faster and more accurately. Note that LML does not limit to a particular machine learning
model. It is more like a general systems approach that can be applied to any machine learning model.
I like the idea of plugging LML to enhance existing models. Really cool.
Brett, let me ask you something I am particularly curious about, regarding the amount of data to learn from, in general.
What do the authors of LML think of big data? Let me be more precise. Do you think the more the better?

<strong>Brett:</strong>
In general, yes. In social sciences such as education, cognitive science, and philosophy, it is common knowledge that like the
“Matthew effect” of the rich get richer, the more you know the more you can learn. The more you know, the easier it is for you
to learn something new. If we do not know anything, it is very hard to learn anything new. These are intuitive as each one of
us must have experienced this in our lives. For example, it is probably impossible to teach a person how to solve differential
equations if the person has only an elementary school education. It is also important to learn from a wide range of domains,
which gives us a larger vocabulary and a wide range of knowledge to be incorporated in learning and problem solving so that it
is easier for us to learn in diverse domains.

<strong>Francesco:</strong>
that’s also true for languages. Learning a new language for a person who already knows 4 or 5 is way easier than a person who
just speaks her native language.

These should be the same for computer systems. To learn and accumulate a large quantity of knowledge, the system needs a large
volume of diverse data. Fortunately, such big datasets are now readily available, which should allow a computer system to learn
and acquire a broad range of knowledge continuously to become more and more knowledgeable, and more and more effective at learning
and problem solving. A significant part of our book focuses on natural language processing and text mining. The reason is that
with the popularity of the Internet, it is fairly easy to collect a large amount of text data from many many distinct websites.
This provides a golden opportunity for an effective LML system.

That’s fine as for the amount of data. How about bias in the data? There is a high number of datasets that are only partially
representing a phenomenon. This not only prevents models from learning but can also lead to very inaccurate models that learn
only one aspect (usually the biased one) of the training data. How does LML overcome such conditions?

<strong>Brett:</strong>
That’s exactly one of the strengths of LML. Let’s first talk about why the regular machine learning approach may suffer from the
bias. If there is bias in the data, which is quite common, a regular machine learning approach attempts to fit the data, and thus
also fit the bias. As a result, the model degenerates due to the skewness of the data. For example, let’s say, we have a collection
of Tweets that only contain positive or neutral polarity towards a specific event. We then train a model on such dataset.
When it comes to the test data, it will wrongly classify the Tweets of negative sentiment because the model has never seen them before.

Let’s see how LML deals with it. At the high level, LML tries to fit the data and the accumulated knowledge. Because it balances the
fitting of data and knowledge, it naturally avoids the issue of data overfitting. On the one hand, we need to fit the knowledge because
we need to correct the bias or skewness of the data. On the other hand, the data is needed to filter irrelevant knowledge from the
accumulated knowledge. Let’s go back to the example of Tweets sentiment classification. Note that LML works with multiple tasks.
Let’s say after the task of Tweets sentiment classification, we get others tasks such as product review rating classification using
Amazon reviews, and movie rating prediction using IMDB reviews. In such case, the LML system will be exposed to many negative reviews
and the expressions of negative polarity. After finishing these subsequent tasks and extracting knowledge from them, the system has
a more comprehensive knowledge about positive, neutral and negative sentiment, which can be used to improve the task of real world
Tweets sentiment classification.
Incremental learning might be very useful in all those cases in which it is not possible to learn everything from scratch.
This is also what online learning does. How does LML distinguish itself from incremental learning?

<strong>Brett:</strong>
I believe you are mainly talking about single-task incremental learning, which is usually called online learning. Let me first
briefly review online learning.

Online learning is a learning paradigm where the training data points arrive in a sequential order. When a new data point arrives,
the existing model is quickly updated to produce the best model so far. Its goal is thus the same as classic learning, i.e., to optimize
the performance on the given learning task. It is normally used when it is computationally infeasible to train over the entire dataset or
the practical applications cannot wait until a large amount of training data is collected.

Although online learning deals with future data in streaming or in a sequential order, its objective is very different from lifelong machine
learning. Online learning still performs the same learning task over time. Its objective is to learn more efficiently with the data arriving
incrementally. Lifelong machine learning, on the other hand, aims to learn from a sequence of different tasks, retain the knowledge learned
so far, and use the knowledge to help future task learning. Online learning does not do these.

Wow, so with Lifelong machine learning, you are basically packing what the model has learned so far, and starts from there rather than from
scratch. And this knowledge can come from learning from different tasks. We’re really talking about humans here :)
Let me mention a potential side effect...
As a matter of fact the major difference, in optimization terms, is local vs global optimization.
Is there any risk that LML would result less accurate because it never gets the full picture of the problem?

<strong>Brett:</strong>
The idea of local vs. global optimization is similar in LML. The main difference is that the objective function is distinct because it
takes the knowledge into consideration. As the results, the global optima may be different due to different objective functions.
To give you an example, in our ACL 2015 paper, under the naive Bayesian text classification framework, the objective function for sentiment
classification is to maximize the probability difference between the correct label and the other labels. Ideally, if the model is perfect,
it should always predict the probability of the correct label to be 1, and the probability of the other labels to be 0. With the LML
enhancement, the knowledge is added into the objective function as L2 regularization terms. So the optimal solution becomes different.

In terms of risks, yes, there are some cases where LML may suffer. The main one is the integration of inappropriate knowledge.
Note that LML deals with multiple distinct tasks sequentially. Due to the difference among the tasks, the extracted knowledge in the past
may not be applicable to the new tasks. If LML blindly takes all the accumulated knowledge as the groundtruth for the new task, it is
likely to damage the performance. Let’s revisit one example I mentioned before. A word may have multiple senses. For example, in previous
tasks, the word light may only mean “something that makes things visible”. But in a new task, word light may be used with a new meaning
“of little weight”. If the LML system only believes in the knowledge and treats the word light with only one meaning, it will not get it
right in the new task.

<strong>Francesco:</strong>
So how would you select the right knowledge?

<strong>Brett:</strong>
We use different mechanism. For example, in our ICML and KDD paper I mentioned before, we used frequent itemset mining and pointwise
mutual information to approximate the semantic correlation using the new task data. The knowledge is then selected based on how they
correlate to this approximation.
LML takes the distance also from Reinforcement Learning, by which an agent gets rewarded or penalized after a transition to another state
in the environment. This will eventually force the agent to learn an optimal strategy for the task at hand. What is missing here that LML
can provide?

<strong>Brett:</strong>
First of all, let me talk about reinforcement learning and then its difference from LML.

Reinforcement Learning is the problem where an agent learns actions through trial and error interactions with a dynamic environment.
In each interaction step, the agent receives input that contains the current state of the environment. Then the agent chooses an action
from a set of possible actions. The action changes the state of the environment. Then, the agent gets a value of this state transition,
which can be a reward or penalty. This process repeats as the agent learns a trajectory of actions to optimize its objective.
The goal of reinforcement learning is to learn an optimal policy that maps states to actions that maximizes the long run sum of rewards.

But, in order to achieve high-quality performance, the agent usually needs a large amount of quality experience. This is particularly
true in high-dimensional control problems. The high cost of gaining such experience is a challenging issue for reinforcement learning.
In the book, we covered lifelong reinforcement learning, which is one type of LML. The motivation  of lifelong reinforcement learning
is to use the experience accumulated from previous tasks to improve the agent’s decision making in the current new task.
The book talks about multiple recent research works that demonstrate the experience or knowledge accumulated from previous tasks,
can significantly save the cost or time when the agent interacts in a new task, where a new task in lifelong reinforcement learning
can be a new environment or a new set of actions and states. Interested reader can refer to Chapter 6 in the book.

<strong>Francesco:</strong>
I must admit that I partially skipped that chapter, I will read right after this episode :)
Do you think unsupervised learning is going to disappear any time soon?
I mean that as collecting data becomes cheaper, and labeled data increase, what would be the point of unsupervised learning at all?

<strong>Brett:</strong>
Actually, I do not agree on this. I believe unsupervised learning will not go away, instead it will become more important.
First of all, I agree that we will have more data, but manually labeling data is still very expensive. For example, in our experience
of sentiment classification, labeling 1,000 Tweets can take several days. This includes finding and training the annotators, sampling a
small subset of data to calibrate the annotators, and a couple of days on labeling the data. At the end, there are some ambiguous examples
which often take hours of discussions to reach a mutual agreement among annotators. And we are just talking about 1,000 Tweets only.
Considering the larger and larger size datasets, having human labeling all of them is infeasible.

Also, in many cases, the user application is not clear. We may just wanna a better understanding of the data. In such case, unsupervised
learning such as clustering is very useful to provide some insights into the data. The information from unsupervised learning are often
fed into supervised learning as features. Recently, there is a trend to study Deep learning based on unsupervised learning.
There has been significantly more research on supervised Deep learning. But researchers have started to notice the importance of unsupervised
learning and devote more time on it. I believe the research of Deep learning and other machine learning approaches on unsupervised
learning will make unsupervised learning more popular and promising. Also, in our book, we have Chapter 4 that covers lifelong unsupervised
learning. It mainly talks about LML on unsupervised topic modeling.

On the other hand many researchers have left autoencoders and unsupervised neural models a bit on the side. I hope that research in
those areas also get more active soon. What are the future directions the authors of LML are taking in machine learning?
I would also be happy to hear about the next big thing in ML, if you have an opinion about that.

<strong>Brett:</strong>
There are many exciting future directions of LML. I want to highlight three of them here.
Correctness of knowledge: we have chatted a bit about it before. How to know whether a piece of past knowledge is correct is crucial for LML.
Because LML leverages past knowledge to help future learning, incorrect past knowledge can be very harmful. Note that LML is essentially a
continuously bootstrapping learning process. Errors can propagate from previous tasks to subsequent tasks and result in more and more errors.
This problem must be solved to ensure that LML is effective. Human beings solve this problem quite effectively. Even if mistakes are made
initially, they can correct themselves later if new evidence is present. They can also backtrack and fix the errors along with the wrong
inferences made based on the errors. An LML system should be able to do the same.
Applicability of knowledge: How to know whether a piece of knowledge is applicable to a new learning task is also critical for LML.
Although a piece of knowledge may be correct and applicable in the context of some previous tasks, it may not be applicable to the current
task due to the wrong context. Without solving this problem, LML will not be effective either. Again, my works in the book proposed some
preliminary mechanisms to deal with the problem in the contexts of topic modeling and supervised classification. However, the problem is
far from being solved. Much research is needed.
Learning with tasks of multiple types from different domains: Much of the current research of LML focuses on multiple tasks of the same type.
In this case, it is easier to make use of past knowledge. If different types of tasks are involved (e.g., entity recognition and attribute
extraction), in order to transfer past knowledge from one type of task to another type, we need to make connections between these types of
tasks. Otherwise, knowledge is hard to use across tasks. One system called NELL (never ending language learner) made some attempts to do
this. Ideally, this should be done automatically. But with the current technology, it is hard because the connection needs to be made via
some higher-level knowledge, which needs to be learned separately.

<strong>Francesco:</strong>
And in cases like this one it’s easy to move the problem somewhere else :) I am personally very excited about LML research and what LML
systems can accomplish in the future. And I am very excited to see and eventually play with such systems too.
Brett it was very nice to have you here at Data Science at Home. Is there a way for our listeners to reach you?

<strong>Brett:</strong>
Best way to contact me is via email czyuanacm@gmail.com and Google searching for my name, Brett Zhiyuan Chen and my publications.
