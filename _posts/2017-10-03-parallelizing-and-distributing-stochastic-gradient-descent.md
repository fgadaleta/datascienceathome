---
title: Parallelizing and distributing Stochastic Gradient Descent
layout: post
---

Continuing the discussion of the last two episodes, there is one more aspect of deep learning that I would love to consider and therefore left as a full episode, that is parallelising and distributing deep learning on relatively large clusters. 
As a matter of fact, computing architectures are changing in a way that is encouraging parallelism more than ever before. And deep learning is no exception and despite the greatest improvements with commodity GPUs - graphical processing units, when it comes to speed, there is still room for improvement.
Together with the last two episodes, this one completes the picture of deep learning at scale. Indeed, as I mentioned in the previous episode, How to master optimisation in deep learning, the function optimizer is the horsepower of deep learning and neural networks in general. A slow and inaccurate optimisation method leads to networks that slowly converge to unreliable results. 
In another episode titled “Additional strategies for optimizing deeplearning” I explained some ways to improve function minimisation and model tuning in order to get better parameters in less time. So feel free to listen to these episodes again, share them with your friends, even re-broadcast or download for your commute. 
While the methods that I have explained so far represent a good starting point for prototyping a network, when you need to switch to production environments or take advantage of the most recent and advanced hardware capabilities of your GPU, well... in all those cases, you would like to do something more.  


Generally speaking, the optimizer is the core component of neural networks, no matter their architecture, represented by the number of layers and neurons per layer.
Under certain conditions Stochastic Gradient Descent is a reliable method that’s why it is still the number one optimisation method in deep learning. In this episode I will explain how can we make it faster by exploiting modern hardware architectures and GPUs. 

Given the ubiquity of large-scale data solutions and the availability of low-commodity clusters, distributing SGD to speed it up further is the next step to take. The major issue however is represented by the fact that SGD by itself is a sequential method. This means that step-by-step, we progress further towards the minimum or the maximum of the loss function, following the direction of the negative gradient. 
Running a gradient descent method provides good convergence but can be slow particularly on relatively large datasets. 
In contrast, running SGD asynchronously can be faster, but suboptimal communication between workers can lead to poor convergence. Multiple workers can optimise with respect to a subset of the entire training set. But if they do not communicate with each other fast enough or with sufficient frequency, such optimisations can be only local, forcing the optimiser towards a local minimum. Additionally, we can also parallelize SGD on one machine without the need for a large computing cluster. 
What follows in this episode is a list of algorithms and architectures - definitely non exhaustive - that have been proposed by researchers to optimize SGD with parallelism and distributed computing in mind.

### Hogwild!
The first algorithm that can improve off-the-shelf gradient descent is called Hogwild. 
Hogwild is an algorithm that takes advantage of data sparsity. The key of this algorithm is that with sparse data, each parameter update will affect only a fraction of all parameters. This in turn leads to  several CPUs updating parameters in parallel with very low chances to interfere with each other and therefore overwriting results. There is however no guarantee that even with sparse data, some parameters will get overwritten, in which case overall convergence will slow down. And so the fact that several CPUs or cores can access shared memory without locking any parameter can play in favor of the algorithm when there is no overwriting. But it can also be quite detrimental in the case in which overwriting occurs.  It is very difficult to take this overwriting into account beforehand. That’s why Hogwild! performs better on some datasets rather than others. Another algorithm that performs parallelization, improving the baseline of SGD is Downpour SGD.


#### Reference
```
Hogwild: A Lock-Free Approach to Parallelizing Stochastic Gradient Descent Benjamin Recht, Christopher Re et al.
Part of: Advances in Neural Information Processing Systems 24 (NIPS 2011) https://papers.nips.cc/paper/4390-hogwild-a-lock-free-approach-to-parallelizing-stochastic-gradient-descent
```


### Downpour SGD
This algorithm comes from the DistBelief framework from which TensorFlow was created and it is basically an asynchronous approach. 
The architecture of Downpour is formed by a server, the parameter server, to which multiple nodes send their parameter updates. Each node runs in parallel on a subset of the training dataset. Each node can be running on the same physical hardware or on different machines. While parallelisation is clearly maximised, since every machine executes a different optimisation problem on substantially different data, parameters can still diverge due to the fact that there is no communication mechanism in place allowing the single node/machine to share their updates with the others. As a consequence convergence can slow down quite consistently or - worse - it could never be reached. 

#### Reference:
```
Large Scale Distributed Deep Networks Jeffrey Dean, Greg S. Corrado, et al. and Andrew Y. Ng NIPS 2012: Neural Information Processing Systems. 
http://research.google.com/archive/large_deep_networks_nips2012.html
```

In this seminal paper, the authors consider the problem of training a deep network with billions of parameters using tens of thousands of CPU cores, and thousands of different model replicas. Of course only a large organisation of the caliber of Google could run such a beast. But this project paved the way to many others, that tackle the problem of asynchronous gradient optimisation. One very famous is definitely TensorFlow that has been open sourced and is becoming kind of a standard also for other machine learning models. One less famous but definitely worth mentioning, DeepDist Lightning-Fast Deep Learning on Spark Via parallel stochastic gradient updates.
The approach of DeepDist is slightly different than the original DownPour and frankly quite interesting.
DeepDist implements Downpour-like stochastic gradient descent. As in the original idea, it starts a master model server and a certain number of nodes in a Spark cluster. Subsequently, on each data node, DeepDist fetches the model from the master and calls the gradient() function. This will compute gradients on the data partitions. Then gradient updates are sent back to the server. But it is only on the server that the master model is updated by the descent() function, that is the actual minimisation. 
It is shown that models can converge faster than other methods because gradient updates are constantly synchronized between the nodes.
The major difference with respect to classic models is that in traditional parallel approaches nodes have to compute all subgradients over the (subsampled) data before they can update the model. Gradient updates are usually much less frequent and deep belief models might converge more slowly. Indeed only at the end of the computational step of gradient and descent the parameters are transferred to the master.


### Delay-tolerant Algorithms for SGD
This is an algorithms that has been applied to distributed systems with large delays between gradient computations and the corresponding updates. Taking inspiration from adaptive gradient methods, for instance AdaGrad, discussed in the episode “How to master optimisation in deep learning“, the authors of this approach develop algorithms that adapt to the sequence of gradients and to the precise update delays that occur. Leaving all the math out for today, what they essentially implement is a way to quantify the impact of the delays. In fact, the key algorithmic technique is efficiently revising the learning rate used for previous gradient steps. It is shown that when this delay grows large (1000 updates or more), this new algorithm performs significantly better than standard adaptive gradient methods.
If you are brave enough to digest all the math, these concepts are explained in the original paper by McMahan and Streeter and also reported in the shownotes. 


#### Reference:
```
Delay-Tolerant Algorithms for Asynchronous Distributed Online Learning
https://static.googleusercontent.com/media/research.google.com/en//pubs/archive/43138.pdf
```


### TensorFlow
TensorFlow has been developed at Google, and as I anticipated it comes from DistBelief architecture. It is one of the de-facto standards accepted by the deep learning community (even though there are many other amazing libraries that are still greatly defending their position in the field, Keras being one in particular). 
Tensorflow looks at an algorithm as a graph of operations that must be performed in a specific order. Some of these operations can be executed in parallel only under certain conditions, such as whenever there are no dependencies with the other parts of the graph.
And so the approach of TensorFlow is to break down the problem of optimisation in small pieces or subgraphs of the entire computation graph of the objective function to minimize. At that point each subgraph is assigned to different devices or machines or even GPUs within the same physical machine that can calculate their subgraph in parallel and return partial results towards the root of the graph. This deals nicely with the synchronisation issues and model parameter updates. Communication among devices occurs via *Send/Receive* mechanism. 

##### TensorFlow can hog a GPU.
On startup, TensorFlow tries to allocate all available GPU memory for itself. And so if you are using the same GPU for something else there might be a hardware conflict and terrible slowdown.

##### Heterogeneous resource utilization adds complexity.
Wheneven you try to optimise and squeeze the hardware to your needs you need to have control on heterogeneous operations manually. For instance, having a multi thread application that fetches and pre-process data and then feeds the GPU, would be extremely helpful because the GPU would not be waiting on such pre-processing operations. However, the level of complexity to manage this scenario is higher.
##### Documentation can be inconsistent.
I personally found a lot of inconsistencies between new functionality and docs/tutorials explaining how to build stuff. This in turn made me frustrated and made my learning curve steeper than expected. There are a lot of tutorials and interesting books to start. But several time it happened that they became obsolete quite quickly.
##### By default, Theano and TensorFlow can conflict.
If you are like me, coding with Theano or have a lot of code that depends on it, from loading data to various utility functions, be aware that Theano and TensorFlow are not good friends. Indeed if you import Theano and TensorFlow in the same scope, they will compete to allocate GPU memory and bad unpredictable things might happen. 

#### Reference
```Original architecture paper https://arxiv.org/abs/1603.04467 Website http://www.tensorflow.org```


### Conclusion
In this episode we looked at strategies to parallelise with modern architectures. 
In the last two episodes I also explained some additional strategies to optimise training in deep learning in general. 
I think that this will be useful in the very near future due to the fact that neural networks get deeper and require longer training time to achieve decent results. In addition as more and more data become available, more domains are being tackled with deep learning techniques. 
Several researchers are also exploring deep learning solutions for mobile devices. Therefore optimisation will become more and more prominent for final users and definitely a priority for researchers.


That’s all for today. Thanks for listening!