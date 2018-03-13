---
title: What deep learning cannot do
layout: post
---

After the AI winter of the 70s, the combination of data and hardware improvements have changed the way researchers tackle the hard computing problems of the century. It seems however that irrational enthusiasm is the main driving force of adoption of deep learning in domains that probably go beyond its capabilities. 
                    
As a matter of fact, deep learning has lighten up the room with successes in image recognition tasks, speech recognition, and language translation. But it also hit some invisible walls confusing a taxi for a dog or a stealth bomber, that no healthy biological brain would have never done.
I hereby present some of the most hidden limitations of deep learning technology, and suggest that deep learning alone is not sufficient to solve the problems of complex domains like finance, and definitely not sufficient to reach artificial general intelligence (AGI), a form of intelligence comparable to the one of humans.
## What is Deep Learning? (very very briefly)
Briefly speaking, deep learning consists in wiring a set of inputs (eg. the image to classify or the sentence to be translated) to a set of outputs (eg. the label of the image or the sentence in another language) and optimising the connections between input and output such that a similar input will be labelled with the appropriate output.  
While one can think this is pure magic, it is really not. What deep learning basically does is creating a mapping, improving it as more and more examples are observed. This is what mathematicians call optimisation methods. 
In a [previous post](http://datascienceathome.com/2017/09/25/how-to-master-optimisation-in-deep-learning/) I explain some of the most used optimisation techniques for deep learning. Additional techniques are described in [another post](http://datascienceathome.com/2017/09/29/additional-optimisation-strategies-for-deep-learning).

Despite the limitations of the optimisation techniques currently used by deep learning, generally speaking, given an infinite amount of data, deep neural networks could represent finite deterministic mappings between any given set of inputs and outputs. But considering such an assumption in practice would be extremely dangerous and irresponsible for designers, researchers and practitioners. The physical world will never be characterised by infinite data and infinite computational resources. Hence, in such a setting, deep learning might be the least appropriate method of all.

## Complexity of Neural Models 
Neural networks are not only complex mathematical objects that can count hundreds of millions of parameters for relatively small problems, but also very difficult to decode and understand their internals. 
Many researchers compare neural networks to black boxes, that are impossible to decipher. This, in turn makes it difficult to adopt such methods in domains like healthcare and finance in which explaining the why can be more important than solving the problem itself.

## Effectiveness of Neural Networks        
Probably the biggest limitation of deep learning technology (as any other statistical function approximation technique) consists in binding the distributions of training and testing data. In simple words, this means that a neural network will generalise well if and only if the testing data (the data where the network is guessing an answer for) has the same statistical distribution as the training data (the data used to create the mapping between input and output). In practice, such a statement says that an image classifier trained on dogs and cats will do a pretty good job on other dogs and cats, but definitely a terrible one classifying anything different. 
All the abstractions that a neural network can learn from a specific training data are limited to the scope of that training data. 
## Incapability to perform inference
As Dr. Gary Marcus stated, deep learning cannot perform open-ended inference that would allow a model to distinguish sentences like *“The general decided to neglect the plan”* and *“The general decided the plan to neglect”* to determine the real intentions of the general. This type of inference is trivial to any human reading text. 

## Debugging and Engineering
While coding neural networks is becoming easier and easier due to many fundamental improvements in libraries like Tensorflow provided by Google, debugging and measuring performance remains a tedious task. A model that is fully data driven is very susceptible to the data. Feeding different or unexpected data can break it.
Moreover, deep learning is more difficult to deploy in production environments with respect to traditional predictive solutions. This is usually due to the size of the models and the hardware requirements that might become prohibitive when scaling to millions of requests. In addition, neural networks require to be tuned and trained as new data feeds in. Training from scratch or continuing training a deployed neural model can be extremely risky due to a phenomenon also known as *“catastrophic forgetting”* that breaks the old mapping between input and output to accommodate the new learned ones. 

## Conclusion
Many consider neural networks magical tools because such methods have been tested on problems that are easy for humans to understand, though difficult to solve with an algorithm. It is easy to understand what an image classifier should be doing. But it was difficult (so far) to build one that performed as good as neural networks do. 
This is a great achievement of course but still far from considering neural networks a miniature biological brain that can solve everything.

The problems of the real world are not just about classifying cats and dogs. Despite what Andrew Ng suggests - “If a typical person can do a mental task with less than one second of thought, we can probably automate it using AI either now or in the near future”  - real world problems are not merely about categorizing objects. They are much more complex and interconnected. While deep learning is good for categorization, it does a much worse job with common reasoning, which is clearly outside the scope of what deep learning is capable of. 

 
### The necessity of hybrid models
One possible solution to overcome the limitations of deep learning lays in the concept of hybrid models. 
As already shown by psychologists like Daniel Kahneman, the human brain relies on multiple systems, namely system 1 and system 2. The former is the fast, automatic, and emotional brain, the latter being a slow, logical, calculating brain. Pretending to simulate a biological brain with a number of layers and linear algebra operations might not only lead to disappointing results but also could bring us one step closer to a new AI winter.



## References
1. https://en.wikipedia.org/wiki/AI_winter
1. Deep Neural Networks for Object Detection http://papers.nips.cc/paper/5207-deep-neural-networks-for-object-detection.pdf
1.  Towards End-to-End Speech Recognition with Recurrent Neural Networks
1. http://proceedings.mlr.press/v32/graves14.pdf
1. Deep Neural Networks in Machine Translation: An Overview http://www.nlpr.ia.ac.cn/cip/ZongPublications/2015/IEEE-Zhang-8-5.pdf
1.  http://www.bbc.com/news/technology-41845878
1.  http://www.evolvingai.org/fooling
1. https://hbr.org/2016/11/what-artificial-intelligence-can-and-cant-do-right-now
1. Thinking Fast and Slow - Daniel Kahneman