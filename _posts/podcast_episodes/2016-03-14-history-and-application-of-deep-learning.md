---
layout: episode
category: podcast
title: History and applications of Deep Learning
date: 2016-03-14
keywords: [big data, neural networks, machine learning, deep learning, AI]
producer: worldofpiggy.com
explicit: No
block: not available
duration: "22:39"
length: 20700000
media: https://s3.amazonaws.com/dshpodcast/media/datascience_episode_deeplearning.mp3
excerpt: What is deep learning?If you have no patience, deep learning is the result of training many layers of non-linear processing units for feature extraction and data transformation e.g. from pixel, to edges, to shapes, to object classification, to scene description, captioning, etc. 
comments: true
---


<img src="https://s3.amazonaws.com/dshpodcast/media/cover.jpg" />


### What is deep learning?

If you have no patience, deep learning is the result of training many layers of non-linear processing units for feature extraction and data transformation e.g. from pixel, to edges, to shapes, to object classification, to scene description, captioning, etc. 

### History

As old as the 80s! Then why this approach has been abandoned for a while? 
The answer is in the lack of big training data and computing power in the early days.
However, five major events occurred in the past and all of them contributed to define and make what we today call deep learning possible.

- **Fukushima's Neocognitron** introduced [convolutional](https://en.wikipedia.org/wiki/Convolution) neural networks partially trained by <a href="https://en.wikipedia.org/wiki/Unsupervised_learning"> unsupervised learning </a> with human-directed features in the neural plane.

- **Backpropagation** <a href="https://en.wikipedia.org/wiki/Yann_LeCun"> Yann LeCun </a> et al. (1989) (* check Errata) applied supervised <a href="https://en.wikipedia.org/wiki/Backpropagation"> backpropagation </a> to such architectures. Weng et al. (1992) published convolutional neural networks Cresceptron for 3-D object recognition from images of cluttered scenes and segmentation of such objects from images.

- **Max-pooling (1992)** appeared to be first proposed by <em>Cresceptron</em> to enable the network to tolerate small-to-large deformation in a hierarchical way, while using convolution. Max-pooling helps, but does not guarantee, shift-invariance at the pixel level. 


People tried to train deep networks and they mostly failed. Why? <a href="https://en.wikipedia.org/wiki/Sepp_Hochreiter"> Sepp Hochreiter </a> 's diploma thesis of 1991 formally identified the reason for this failure as the <a href="https://en.wikipedia.org/wiki/Vanishing_gradient_problem"> **vanishing gradient problem** </a>, which affects many-layered feedforward networks and 
<a href="https://en.wikipedia.org/wiki/Recurrent_neural_network"> recurrent neural networks</a>


#### Pre-training (Geoffrey Hinton) 

Other methods use unsupervised pre-training to structure a neural network, making it first learn generally useful 
[feature detectors](https://en.wikipedia.org/wiki/Feature_detection_(computer_vision)).
Then the network is trained further by supervised [back-propagation](https://en.wikipedia.org/wiki/Back-propagation) to classify labeled data. 
The deep model of Hinton et al. (2006) involves learning the distribution of a high-level representation using successive layers of binary or real-valued 
<a href="https://en.wikipedia.org/wiki/Latent_variable">latent variables</a>. 
It uses a <a href="https://en.wikipedia.org/wiki/Restricted_Boltzmann_machine">restricted Boltzmann machine</a> (Smolensky, 1986) to model each new layer of higher level features. 
Each new layer guarantees an increase on the <a href="https://en.wikipedia.org/wiki/Lower_bound">lower-bound</a> of the <a href="https://en.wikipedia.org/wiki/Log_likelihood">
log likelihood</a> of the data, thus improving the model, if trained properly.

Looks like a tongue-twister, right? Well, it basically says that if trained well, a network can generate data that are similar to the ones that were fed from the training set. 
Once sufficiently many layers have been learned, the deep architecture may be used as a <a href="https://en.wikipedia.org/wiki/Generative_model"> generative model</a> by 
reproducing the data when sampling down the model (an <em>"ancestral pass"</em>) from the top level feature activation. Hinton reports that his models are effective feature 
extractors over high-dimensional, structured data.



#### What are vanishing gradients?
Recurrent networks are trained by unfolding them into very deep feed forward networks, where a new layer is created for each time step of an input sequence processed by the network. 
As errors propagate from layer to layer, they shrink exponentially with the number of layers, impeding the tuning of neuron weights which is based on those errors (LSTMs were 
proposed as a solution in 1997)




### And now, the power of deep learning

One of the promises of deep learning is replacing handcrafted <a href="https://en.wikipedia.org/wiki/Feature_(machine_learning)">features</a> with efficient algorithms for 
<a href="https://en.wikipedia.org/wiki/Unsupervised_learning">unsupervised</a> or <a href="https://en.wikipedia.org/wiki/Semi-supervised_learning">semi-supervised</a> 
<a href="https://en.wikipedia.org/wiki/Feature_learning">feature learning</a> and hierarchical <a href="https://en.wikipedia.org/wiki/Feature_extraction">feature extraction</a>.

For <a href="https://en.wikipedia.org/wiki/Supervised_learning"> supervised learning </a> tasks, deep learning methods obviate 
<a href="https://en.wikipedia.org/wiki/Feature_engineering">feature engineering</a>, by translating the data into compact intermediate representations akin to 
<a href="https://en.wikipedia.org/wiki/Principal_Component_Analysis">principal components</a>, and derive layered structures which remove redundancy in representation. 
Moreover, PCA is a linear method that will ignore non-linearities of the data. Many deep learning algorithms are applied to 
<a href="https://en.wikipedia.org/wiki/Unsupervised_learning">unsupervised learning</a> tasks. 
This is an important benefit because unlabeled data are usually more abundant than labeled data eg. <em>autoencoders.</em>


### Links

[Build your deep learning machine](http://timdettmers.com/2015/03/09/deep-learning-hardware-guide)


[Build your deep learning machine](http://graphific.github.io/posts/building-a-deep-learning-dream-machine) 

**Google photos** search [images by text](http://gizmodo.com/google-photos-hands-on-so-good-im-creeped-out-1707566376)

[Automatically color bw images](http://tinyclouds.org/colorize)

[Teradeep real-time object classifier](https://www.youtube.com/watch?v=_wXHR-lad-Q) like Terminator 1984




### Errata

As Paul P. suggested, Rumelhart, Hinton, and Williams should be credited with discovering back-propagation, not LeCun.

References are from [Hinton Backprop](https://www.cs.toronto.edu/~hinton/backprop.html) 

Rumelhart, D. E., Hinton, G. E., and Williams, R. J. (1986) Learning representations by back-propagating errors. Nature, 323, 533--536


Hinton, G. E. (1986) Learning distributed representations of concepts. Proceedings of the Eighth Annual Conference of the Cognitive Science Society, Amherst, Mass. Reprinted in Morris, R. G. M. editor, Parallel Distributed Processing: Implications for Psychology and Neurobiology, Oxford University Press, Oxford, UK


Rumelhart, D. E., Hinton, G. E., and Williams, R. J. (1986) Learning internal representations by error propagation.
In Rumelhart, D. E. and McClelland, J. L., editors, Parallel Distributed Processing: Explorations in the Microstructure of Cognition. Volume 1: Foundations Volume 1: Foundations, MIT Press, Cambridge, MA.


