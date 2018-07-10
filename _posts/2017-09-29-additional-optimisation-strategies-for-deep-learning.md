---
title: Additional optimisation strategies for deep learning
layout: post
summary: In this episode I would like to continue that conversation about some additional
  strategies for optimising gradient descent in deep learning and explain some tricks
  that might come useful when your neural network stops learning
comments: true
---

<iframe src="https://www.podbean.com/media/player/p54dv-73d2ee?from=yiiadmin&skin=1&btn-skin=104&share=1&fonts=Verdana&auto=1&download=0&rtl=0" scrolling="no" data-name="pb-iframe-player" width="100%" height="100" frameborder="0"></iframe>

<br />

In the last episode [“How to master optimisation in deep learning”](https://www.podbean.com/media/share/pb-y75qj-700faa) I explained some of the most challenging tasks of deep learning technology together with methodologies and algorithms to improve the speed of convergence of a minimisation method for deep learning.
I explored the family of **gradient descent methods** - definitely not exhaustively - giving a list of approaches that deep learning researchers are considering for different scenarios. Every method has its own benefits and drawbacks, pretty much depending on the type of data, and data sparsity. However, there is one method that seems to be, at least empirically, the best approach so far.
Feel free to listen to the [previous episode](https://www.podbean.com/media/share/pb-y75qj-700faa), share it, re-broadcast or just download for your commute.

In this episode I would like to continue that conversation about some additional strategies for optimising gradient descent in deep learning and explain some tricks that might come useful when your neural network stops learning from data or when the learning process becomes so slow that it really seems it reached a plateau even by feeding in fresh data.
Let's start from curriculum learning.


### Shuffling and Curriculum Learning
In order to train a neural network, practitioners usually randomly selects observations in order to feed the model, which will start training and optimising the loss function (that means tuning model parameters) as mentioned in the last episode.
Usually, shuffling samples is a good practice to perform, moving from one learning epoch to another. However, there are some cases in which feeding the network with observations in a specific order seems to work better than simply shuffling them.
Since a better training procedure usually leads to faster optimisation and, in turn, better model parameters it is interesting to understand when the order of observations can make a difference.
Such cases are those in which samples become more and more difficult to predict, a bit in the flavor of adaptive learning methods that indeed adapt according to how difficult it is to classify certain observations. So these models start learning from easy cases and keep learning on cases that are harder and harder to classify or regress (if the model is a classifier or a regressor). And so while there is not really a theoretical explanation of why is that the case, it has been shown empirically that in such pathological situations, forcing the network to learn from samples that are harder and harder to predict seems to improve performance and speed. This method goes under the name of **Curriculum Learning**.

To be fair, however, the authors showed such training capabilities with an LSTM network that has sequential order by design. LSTM networks are indeed considered for Natural Language Processing tasks in which every word is represented in a contextual window of preceding words. In such cases it is quite normal to think that maintaining a specific order in the sequence might be beneficial to the network with respect to a more - let’s say - randomised or shuffled approach.

The very first approach has been proposed in *Curriculum learning,  Yoshua Bengio et al. 2009*. The hypothesis at the time of publication was that curriculum learning had both an effect on the speed of convergence of the training process to a minimum and, in the case of non-convex criteria, on the quality of the local minima obtained. Basically curriculum learning could be seen as a particular form of continuation method (which is a general strategy for global optimization of non-convex functions).

The most recent paper about curriculum learning is *Automated Curriculum Learning for Neural Networks Alex Graves et al. 2017* in which the authors introduce a method for automatically selecting the path that a neural network follows through a curriculum so as to maximise learning efficiency.
They consider two distinct indicators of the learning progress:

1. rate of increase in prediction accuracy, and
2. rate of increase in network complexity

Then path is determined automatically by an algorithm that is driven by a reward that is the amount that the network learns from each data sample. Experimental results for LSTM networks show that this approach can accelerate learning, in some cases halving the time to convergence.

### References:
```
Curriculum learning,  Yoshua Bengio et al.
ICML '09 Proceedings of the 26th Annual International Conference
on Machine Learning

Automated Curriculum Learning for Neural Networks
Alex Graves et al. 2017 https://arxiv.org/abs/1704.03003
```


Another method that can make convergence to the minimum faster and therefore improve the quality of the model parameters is called **Batch Normalisation**

### Batch normalization
Before explaining what batch normalisation can do, let me explain one additional issue that might occur during training deep neural networks. With deep networks the distribution of each layer’s inputs can change quite consistently, due to the fact that as the inputs change, the model parameters keep changing too, during training. In order to deal with constantly changing parameters, a deep learning programmer can set lower learning rates. But lower learning rate will slow down convergence and therefore make learning slower.
It seems that we cannot escape this fundamental problem between changing parameters and learning rates.
This phenomenon is even more emphasised with saturating nonlinearities across layers in deep networks. It has been shown how, by initialising values of parameters with zero mean and unit variance (which goes under the name of *normalisation*) and by updating them as training progresses for every mini-batch, and then back-propagating them too, it is possible to use higher learning rates, and to pay less attention to the initial values of the parameters. This not only makes learning more robust but also speeds up the training as higher learning rates need less iterations to converge to a minimum. Moreover, batch normalisation acts as a regulariser, requiring less dropout and discouraging overfitting.

### References
```Batch Normalization: Accelerating Deep Network Training by Reducing Internal Covariate Shift Sergey Ioffe, Christian Szegedy
https://arxiv.org/abs/1502.03167 ```

Now let’s focus on another method the mitigates the problem of overfitting and is referred to as **Early Stopping**.

### Training early stopping
A common practice to avoid overfitting and to avoid training a neural network more than needed, consists in stopping the training procedure before overfitting actually occurs. Detecting when a network is starting to overfit the data, is not an easy task and one of the few methods to detect when the network is not learning anything new about the data consists in observing the validation error, calculated on the validation set.
If the validation error is not improving that is usually a clear sign that additional training will not add anything new to the current model parameters. So, switch off that GPU and be happy with the current accuracy. Improving the current model would be possible only by changing its architecture or by extending the training set with fresh data.

### Adding gradient noise
In order to improve learning and reduce time of convergence, many researchers rely on newer network architectures or better activation functions in the neurons. There is however an easier solution with lower overhead. This solution consists in adding gradient noise following the Gaussian distribution to each gradient update. The authors of this method show how this technique reduces overfitting, due to randomisation, and sometimes it also leads to lower training loss, which means better optimisation. The scientific explanation of such phenomenon, that indeed sounds a bit too *probabilistic*, is that by adding noise they give to the model more chances to escape and find new local minima, a bit in the flavor of simulated annealing for those who are familiar with Markov chains. Also in that method indeed it is possible to escape local minima by restarting minimisation from a random location in the function space and hope that - by chance - the minimiser will start exploring a space far from the local minimum, if any.

This improvement makes a lot more sense for high dimensional problems and very deep architectures. The authors tried this approach on a fully-connected 20-layer deep network, first trained with standard gradient descent and poor parameter initialisation. Adding noise reduced error rate by 70%, which doesn’t sound that random, after all.
More details can be read from their paper published in 2015 with title *Adding Gradient Noise Improves Learning for Very Deep Networks.*

### Reference
```Neelakantan, A., Vilnis, L., Le, Q. V., Sutskever, I., Kaiser, L., Kurach, K., & Martens, J. (2015). Adding Gradient Noise Improves Learning for Very Deep Networks, 1–11.
Retrieved from http://arxiv.org/abs/1511.06807```

That’s all for today.
With this post you should know a bit more about optimisation strategies for deep learning.
You can listen, share, or re-broadcast to the [podcast episode](https://www.podbean.com/media/share/pb-p54dv-73d2ee).
Enjoy the show.