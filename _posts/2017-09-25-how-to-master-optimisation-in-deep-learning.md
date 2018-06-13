---
title: How to master optimisation in deep learning
layout: post
summary: "The secret  behind deep learning is not really a secret. It is *function optimisation*.
What a neural network does, is optimising a function. For instance, let’s take the image classifier example..."
comments: true
tags:
- optimization
- AI
- deeplearning
- datascience
- neural networks
---

> You can listen to the podcast episode of this post from our [podcast page](https://www.podbean.com/media/share/pb-y75qj-700faa)
> Feel free to download, re-broadcast and share. Enjoy the reading!


<hr>
### Introduction
The secret  behind deep learning is not really a secret. It is *function optimisation*.
What a neural network does, is optimising a function. For instance, let’s take the image classifier example. A network is fed with an image and a label. What the network actually does during training is setting a high number of parameters such that given a similar image, it will return a similar label (or actually the same label). So where’s the optimisation?
Optimisation means minimising or maximising a function. In this case, the function is the difference between the predicted value and the true value. This function is usually referred to as the loss function.

**First-order** methods minimize or maximize the function (in our case the loss function) using its gradient. The gradient is a multi-variable generalization of the derivative. It is a vector-valued function, as opposed to a derivative, which is scalar-valued. Like the derivative, the gradient represents the slope of the tangent of the graph of the function. The most widely used first-order method is Gradient Descent and its variants, as illustrated and explained later.

**Second-order** methods use the second derivative (*Hessian*) to minimize or maximize the loss function. Since the second derivative is costly to compute, one of the most performant second-order method, L-BFGS (Limited-memory Broyden–Fletcher–Goldfarb–Shanno) uses an approximation of the Hessian.
It turns out that computers are very good at minimising only a specific family of functions, so called convex functions. All other cases are just trouble makers.


### When is a function convex?
In order to explain the convexity of mathematical functions, think about a large drinking cup and a ball. Now let the ball roll from the border of the cup. Obviously, the ball will roll down towards the bottom of the cup, then it will oscillate a bit, eventually landing towards the lowest point of the cup. This is called *the minimum*, and the mathematical function that describes the cup is a convex function.
It turns out that the minimum in this case is also global minimum. In fact, the ball cannot go lower than that. Moreover, there is just one such point. The ball cannot go anywhere else. The minimum is global and it is unique. And all this is possible just because the function of the drinking cup is **convex**. If it were not, the ball could have been into a local minimum and we would have never known if there were other minima somewhere else, lower than the current one.
Now back to neural networks.
The drinking cup is the loss function of the differences between the predicted value and the true one. If that function is convex, finding a minimum is going to be a piece of cake for any algorithm. While convexity is a convenient property that plays an important role in function optimisation, many real world examples do not always have such properties.

The horsepower of any neural network, regardless of their architecture, and number of neurons, is the function optimiser that will tune all the parameters of the network. This component is the only part of a neural network that will determine how fast the training procedure is and how accurate the network will predict over new samples. Most of research in deep learning has been spinning around exactly this component, the optimiser, which is very well known to computer scientists and mathematicians.

**Gradient descent** is one of the most popular algorithms to perform optimization and by far the most common way to optimize neural networks. At the same time, every state-of-the-art Deep Learning library contains implementations of various algorithms to optimize gradient descent.
Gradient descent is a way to minimize an objective function J(θ) parameterized by a model's parameters θ∈ℝby updating the parameters in the opposite direction of the gradient of the objective function ∇θ w.r.t. to the parameters. The two ingredients to keep an eye on are the direction towards which to minimize and the learning rate. The learning rate η determines the size of the steps we take to reach a (local) minimum. In other words, we follow the direction of the slope of the surface created by the objective function downhill until we reach a valley.

### Batch gradient descent
This approach computes the gradient of the cost function with respect to the parameters θ for the entire training dataset. As it is required to calculate the gradients for the whole dataset in order to perform just one update, batch gradient descent can be very slow and is intractable for datasets that don't fit in memory.

### Stochastic gradient descent
Stochastic gradient descent (SGD), in contrast, performs a parameter update for each training example x(i) and label y(i). SGD avoids performing one update at a time. It is therefore usually much faster and can also be used for online learning. However, due to the frequent updates the objective function it can fluctuate quite heavily.

### Mini-batch gradient descent
Mini-batch gradient descent finally takes the best of both worlds and performs an update for every mini-batch of n training examples.

In any case, choosing a proper learning rate can be difficult. A learning rate that is too small leads to painfully slow convergence, while a learning rate that is too large can hinder convergence and cause the loss function to fluctuate around the minimum or even to diverge.
Learning rate schedules try to adjust the learning rate during training by e.g. annealing, reducing the learning rate according to a pre-defined schedule or when the change in objective between epochs falls below a threshold. These schedules and thresholds, however, have to be defined in advance and are thus unable to adapt to a dataset's characteristics.
The same learning rate applies to all parameter updates. If the data at hand is sparse and its features have very different frequencies, it might be inappropriate to update all of them to the same extent, rather performing a larger update for rarely occurring features.


## Gradient descent optimization algorithms
SGD has trouble navigating areas of the function to minimise where the surface curves much more steeply in one dimension than in another. This is quite common around local optima.
The method that uses **momentum** can mitigate such issue.

**Momentum** is a method that accelerates SGD in the relevant direction and reduces further oscillations in other directions. The momentum term increases the speed of convergence in certain dimensions where gradient is pointing in the same directions and reduces updates for dimensions whose gradients change directions. That's how oscillations are reduced while going faster.

### Adagrad
Adagrad which stands for Adaptive Gradient adapts the learning rate to the parameters, performing larger updates for infrequent parameters and smaller updates for frequent ones. The major issue of Adagrad is that it accumulates the squared gradients in the denominator. This will keep growing, making the learning rate smaller and smaller as the algorithm proceeds. At some point the algorithm will stop learning because the step will become infinitely small to have no more progress.

### Adadelta
Adadelta solves the issue of Adagrad with the gradient clipping feature that restricts the accumulated past gradients to a fixed number that cannot explode and make the learning rate infinitesimally small.

### Adam (ADAptive Moment Estimation)
This method calculates adaptive learning rates for each parameter. Adam keeps an exponentially decaying average of past squared gradients and of past gradients too in a similar fashion to momentum.
These too averages are estimates of the first moment (the mean) and the second moment (the uncentered variance) of the gradients respectively. In the original paper, the authors empirically show that Adam convergences as expected from the theoretical analysis. Indeed the authors applied Adam optimizer to the logistic regression algorithm on the MNIST character recognition and IMDB sentiment analysis datasets, a Multilayer Perceptron algorithm on the MNIST dataset and Convolutional Neural Networks on the CIFAR-10 image recognition dataset.

### Which optimizer should you choose?
While this is not meant to be a post that exhaustively explores all the aspects of function minimization for deep learning, there are some fundamental guidelines that should be consider to improve the accuracy of a deep learning model and definitely increase the speed of convergence.
If input data is sparse, one should consider one of the adaptive learning-rate methods. As a consequence it will not be necessary to tune the learning rate to achieve the best results with the default value.

Adadelta, and Adam are mathematically very similar and therefore they are expected to have similar results in similar scenarios. While only empirically, Adam is without any doubt the best of all the adaptive algorithms and keeps improving at the end of the optimization when the gradients become sparser. So, Adam might be the best overall choice.

Generally speaking SGD will get to the minimum, even though it might struggle a bit near saddle points, taking longer to converge. In such cases random initialization and annealing schedule strategies can improve convergence quite a lot. As a general rule, while SGD is good and reliable for simple networks, whenever you are dealing with more complex and deeper networks you should choose one of the adaptive learning rate methods for a faster convergence.

I hope you enjoyed the post. Happy optimization!
