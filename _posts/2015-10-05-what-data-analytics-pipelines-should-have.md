---
layout: post
title: What data analytics pipelines should have
tags: [analytics, bigdata, data, engineering, feature, pipeline, visualization]
comments: true
type: post
---

Big data analytics not only means crunching algorithms over high dimensional
data for weeks. It also means preparing the data to get processes with more or
less standard tools. A common pipeline that every data scientist should follow
is reported below. Order of operations matters, even though for some special
cases some can be anticipated or postponed. Here are five steps that a good
analytic pipeline should include. Below this list, an infographic shows the
steps of a good analytic pipeline and the amount of time/resources that should
be spent for each one.

<img src="https://s3-eu-west-1.amazonaws.com/wopcontent/uploads/2015/09/Data-analytics-pipeline1-410x1024.jpg" width="100%" />
*Data analytics pipeline and amount of time/resources that should be spent in each step.*


### Step 0: formulate the problem

This is probably the most difficult step. A problem should be formulated
before collecting data, in order to collect the right type and amount. In case
of verifying hypotheses, data have already been collected. Formulating a
realistic and clear hypothesis is the equivalent of a well-posed problem. Many
managers, investigators, or wannabe bosses fail miserably at this stage,
thinking about some magic in big data that will eventually clarify things
later. Usually this attitude leads to wasting time for the boss and for the
data scientist. 

### Step 1: data wrangling (also referred to as carpentry or cleaning)

Data are ready to be processed only in very rare cases. Usually, when a
problem has been formulated, data get collected in a raw, unstructured form.
For instance, images, which many consider well structured (number of pixels
are known beforehand), can also be interpreted as totally unstructured for
those who are interested in selecting visual features. The same applies to
audio data, data that have been integrated from heterogenous sources, or
parsing free-form text for text mining or sentiment analysis. Cleaning and
normalization usually take place in this first stage of the pipeline.


### Step 2: visualization

If an image is worth a thousand words, this is also true for data
visualization. Visualization is very often one of the first formal steps of
any analytic pipeline. The goal is to find efficient graphical representations
that will summarize the data at the best and emphasize their characteristics.
High dimensional data are challenging to visualize and affected by the
limitations of screens and image resolution. One stratagem that Google
mastered a while ago is a hierarchical form of visualization, typical of
Google Maps.


### Step 3: dimensionality reduction

Not all the dimensions of a dataset are fundamental to represent the hidden
geometry of data. Some dimensions are usually not necessary, redundant or just
highly correlated to others, and can be removed at least for the sake of
visualization. Reducing the dimensionality of the data is a fundamental step
that reduces storage space, makes data more controllable, sometimes more
interpretable to humans, and definitely easier to visualize. Moreover, any
machine learning algorithm might have better performance on a reduced dataset.
The only limitation of dimensionality reduction is the lossy nature of the
compression. Sometimes important aspect of data can be loss during this step.
While sparsity and regularization procedures can deal with number of
parameters higher than number of observations, they should be used with care. 


### Step 4a: feature engineering

Determining which features are going to be considered during the analysis is
essential. This step is usually referred to as feature engineering and
consists in selecting features that might contain information or create new
features from existing ones in order to capture non-linearity or higher order
interactions within the data. As a matter of fact, a well engineered dataset
analysed by a very simple linear regression model can reveal much more
insights than a raw dataset analysed with a fancy complex model. 

### Step 4b: automatic feature engineering

Not everyone really need to include this step in their analytic pipeline. But
many are considering it as a fundamental asset. Automatic feature engineering
is closer and closer to the concept of deep learning neural networks. Deep
learning allows the creation of features in hierarchical fashion. This
representation can explain more and more complex aspects of data. In fact,
deep learning found its main application in artificial vision and natural
language processing, due to the hierarchy of concept representation. Pixels
are grouped to represent lines and points that in turn represent shapes, that
represent objects that represent a scenario, that can finally be understood
and described. Similarly, characters form words that form phrases that
represent concepts that can analysed, and understood by machines. 

### Step 5: state of the art machine learning

This is the step in which off-the-shelf algorithms can be applied, according
to the problem to solve. For instance, unsupervised clustering for labeling
data, decision trees for training a classifier, distribution fitting to
estimate the structure of the dataset at hand. This step is problem specific,
but after the previous operations, any algorithm should perform better here.

Happy analytics!

