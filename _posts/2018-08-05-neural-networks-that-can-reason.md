---
title: Neural networks that can reason
layout: post
summary: |-
  Today’s episode  will be about deep learning and reasoning. There has been a lot of discussion about the effectiveness of deep learning models and their capability to generalize, not only across domains but also on data that such models have never seen.
  But there is a research group from the Department of Computer Science, Duke University that seems to be on something with deep learning and interpretability in computer vision.
comments: 'True'
---

<img src="/img/img_posts/neural_pathways.jpg" height="300px">
<hr />

<iframe src="https://www.podbean.com/media/player/4nv8e-9646b4?from=yiiadmin&skin=1&btn-skin=104&share=1&fonts=Helvetica&auto=0&download=0&rtl=0" scrolling="no" data-name="pb-iframe-player" width="100%" height="100" frameborder="0"></iframe>

Thanks for tuning in and welcome to data science at home podcast, where we talk about technology, machine learning and algorithms.  
Today’s episode  will be about deep learning and reasoning. There has been a lot of discussion about the effectiveness of deep learning models and their capability to generalize, not only across domains but also on data that such models have never seen.
But there is a research group from the Department of Computer Science, Duke University that seems to be on something with deep learning and interpretability in computer vision.

**I am here with Chaofan Chen, Oscar Li, Alina Barnett, Cynthia Rudin from Duke and Jonathan Su from MIT Lincoln Laboratory. Hi everyone. How are you?**

Great! Thanks for having us!

**What type of research do you guys do at Duke University? Is it mainly AI and deep learning oriented?**

Cynthia: I run the prediction analysis lab at Duke, which is mostly focused on interpretable machine learning. We have a lot of projects that are not deep learning actually. Computer vision is something new for us, but we were doing it to prove a point. A lot of people assume that there is a tradeoff between accuracy and interpretability.  So that if you want a really accurate model, they think you have to create a  black box. But that really isn’t true.  So our goal here was to create an interpretable model for computer vision that  is as accurate as any black box computer vision model.

**The project we are referring to in this episode is described in a paper titled “this looks like that: deep learning for interpretable image recognition”.
Let’s start describing the project in more detail. 
When we watch something, we are used to make comparisons and say things like “this animal looks like that other animal I don’t recall the name, or that face really reminds me of that other guy” 
How do humans interpret images?**

Cynthia: Well, let’s think about situations where people need to describe to others how they identify some  object in an  image. Often what they do is they take the image, and put arrows all over the picture pointing out what aspects of the picture we’re supposed to be looking at and why. Like for bird watching, people have to identify what type of bird they are looking at, so they label the different parts of the bird, like “this looks like a goldfinches’ beak” and this looks like the crown of a woodpecker, or whatever. You can see these kinds of images with arrows for identifying what architectural style a house is, and they do this in medicine in radiology for analyzing medical images, they do this for microanalyzing facial expressions, it’s how humans often explain to each other why this thing is what it is, because *it* looks like that *other thing* that I’ve seen before. 


**What is the main goal of this project?**

Cynthia: We wanted to have the algorithm first , be accurate, but also explain its classification of images the same way humans do - by picking out parts of the image and telling us that it’s classifying  something in a particular way because it  thinks this looks like something it’s seen before, and showing us what that is.

Chaofan: The model will automatically learn a set of image patches whose presence or absence is most indicative of the presence or absence of a certain class. This set of prototypical image patches will serve as the “cases” each image will be compared against. This classification process resembles that of a case-based reasoning.


**How different is this approach from a more traditional one in which the goal - in the case of a classifier - is to find the best input that maximises a specific class?**

Oscar: Are you talking about activation maximization? That’s a posthoc method, where you first train a deep learning model and figure out afterwards what it’s doing. In contrast, our network actually explains its own reasoning process. It says “I think these parts of the image look like these parts of images I’ve seen before, and I’m going to use that information to make my prediction.” The network itself is actually interpretable, which isn’t posthoc. 

Follow on [Jonathan]: This approach builds in interpretability from the start instead of trying to come up with an approximate explanation afterwards.  It modifies the network architecture and the objective function to support interpretability, so the explanation one gets describes what the network is really doing.  I suppose one could say that the difference is that instead of making up an explanation for the network, we’re making the network explain itself.

**Can you explain the idea of having prototypes and identifying parts of images to such prototypes to perform classification?**

A: Jonathan: During training, the network learns prototypical image parts, and it learns to use a sparse combination of parts to contribute to each class.  The parts are spread out across the training set so they cover it, and each part matches some part of a training image.  For example, the network might learn parts like a tire, windshield, door, wing, and jet engine.  The sparse combinations mean the network doesn’t use every part for every class, and the presence of a part can encourage or discourage a class.  For example, the network might learn to use the tire, windshield, and jet engine for the car class, and it might learn to use the tire, wing, and jet engine for the airplane class.   Now, what does a jet engine have to do with a car?  Not much, but the network can learn that the presence of a jet engine part discourages the car class and encourages the airplane class.

Add on Alina:
For example, the model learns prototypes like the red wing of the red-winged blackbird or the yellow throat of a yellow-throated warbler. Then when it classifies a new image, it looks for patches similar to the prototypes. So the network can tell you something like “this throat patch from the new image looks like that yellow-throated warbler patch from the training set.” 

**In attention based mechanisms, a model is able to focus on a certain region of an image with “higher resolution” and perceiving the rest in “lower resolution”, such that only specific regions are indeed considered for classification or prediction in general. 
How does your approach differ from attention mechanisms in deep learning?**

Chaofan: There are indeed connections between our model and attention models. When classifying an unseen image, our network computes a similarity map between its patches and each of the prototypes, and this similarity map can be interpreted as a coarse-grained attention map, where the highly activated region on this similarity map indicates something similar to the prototype has been detected on the original image.

Oscar: When making the final decision, our network will only use the strength of the most similar patches as the supporting evidence. In this way we can also view our network as focusing its attention only on regions which it thinks are the most helpful.

Cynthia: It’s sort of like k-nearest neighbors, but more like nearest parts of special neighbors, which are prototypes.

**Another common ground I found is the one with generative models. In such models one can generate a “similar” input and then project it to a lower dimensional space for classification. We could briefly say that a combination of unsupervised-supervised approach is used in that case. How does your approach differ from generative models?**

Alina: We aren't generating any similar inputs, it's solely a discriminative model. As for supervised and unsupervised, we would generally call this a supervised approach because our training data is all labeled. 

Follow on:
Cynthia: This paper isn’t generative, but we some of the past work we’ve done in this area solves a similar problem with using prototypes or parts of neighbors, and does use generative models, and can be used for  unsupervised learning. I have a paper with Been Kim and Julie Shah from NIPS 2014 called the Bayesian Case Method that does this sort of thing for categorical data without neural networks, and there’s a new followup paper with Ramin Moghaddass on this, called Bayesian Patchworks, where each new observation is modeled as if it were generated from parts of other parent observations. We  can generate just x without y, so it can be supervised or unsupervised.

**Speaking about the network architecture, you have implemented this approach with convolutional neural networks. Does the approach generalize to other architectures too?**

Cynthia: Yes, the approach definitely generalizes! We have actually several papers on this basic idea of comparing a new test observation to parts of past observations that don’t involve neural networks even. I mentioned the work we’ve done on Bayesian Case Method and Bayesian Patchworks, but also there’s a paper with Tong Wang that identifies crime series by looking at whether some subset of features of a crime define a modus operandi of a criminal that we’ve seen before. So you can do this type of model for pretty much any setting.

Chaofan: Speaking of generalizing to other architectures, we could attach our prototype layer to any deep neural network. For example, we could include our prototype layer in a fully-connected network, and treat prototypes as one-dimensional vectors in the latent space, that the output of a fully-connected layer can compare against.

**How did you evaluate this approach? How would you claim it improves over traditional CNNs?**

Oscar: Because our special prototype layer can substitute a fully connected layer in the final stage of a standard CNN, we have conducted multiple ablation studies that compare our model with standard CNNs which have the same architecture except for the last layer. What we have found is that in general our model performs about equally well while providing that extra level of explanation.

Follow-on [Jonathan]: In addition, CNNs are often highly over-parameterized, so there’s potentially room to include other constraints without sacrificing accuracy. In our case, the added constraints could help shape the latent space as well as reduce overfitting.

**Do you think this method could be applied to other types of data and predictions, not just images? For instance, would it be possible to consider it for language models?**

Alina: This method uses L2 distances, prototypes and patches. Classifying using L2 distance in the latent space can be readily applied to a variety of data types. No matter the input, if there's a latent space, we can calculate L2 distances. Deciding what a “patch” or “part” is and how to isolate is just different for non-image inputs. For NLP you can just use parts of sentences. We haven’t done that yet though.

**What’s in the future of “this looks like that”?**

Cynthia: We’ve been working with some Duke undergraduates to apply it to medical images and some other high stakes decision making problems, but mostly medical images. We also have a lot of ideas up our sleeve on how to build on our framework; we’ve been working on this problem for a year and a half now so we’re really getting into it! It’s a fun problem.


**If you want you can share your contacts so that people/researcher can reach out**

A: Cynthia: Our group has a website, where people can find our contact information:
https://users.cs.duke.edu/~cynthia/lab.html