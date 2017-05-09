---
layout: post
title: Why is principal component analysis a bust for genetics
comments: true
tags: [bigdata, genetics, pca, principal component analysis, statistics]
---

I am not a fan of Principal Component Analysis. At least not for **big data**
analysis. I still find it awkward to apply such concepts to, e.g. genetic
data. 

As a brief explanation, given variables $$ x_1 \dots x_p $$, a
principal component is a linear combination of some of these variables that
maximise variation of the data. So far, so good. PCA is widely used in genetics 
for variable selection problems. 
Detecting the components of high variation in the data seems to be a good strategy to
discard all those variables that, in contrast, do not. Never sounded so wrong
to me! I have the impression that PCA is considered whenever researchers have
no clue of how to tackle the problem under investigation. Maybe that's the
reason why they consider PCA as being part of the so called _exploratory research_ realm. 
That might seem a good starting point. Not when it becomes
misleading and makes things worse. Let me explain.  In the case of gene
expression profiles, PCA is performed to find those genes that vary the most
across experiments. Therefore, once the linear dependent components have been
identified (in the form of **loadings** or weights), the original data are
projected onto a lower dimensional space. 

In order to overcome the ambiguity
of english words, here is an example that I used to clarify the concept to my
buddy. 
[![Image](https://s3-eu-west-1.amazonaws.com/wopcontent/uploads/2014/05/pca_explained.jpg?w=650)](https://s3-eu-west-1.amazonaws.com/wopcontent/uploads/2014/05/pca_explained.jpg) 

Let's be practical and do it in R.
Assume to have a set of microarray experiments as a $ n times p$ matrix, where
$$ n$$ is the number of samples and $$ p $$ is the number of probes or genes. We
want to identify those genes in the direction of maximum variation. We use the
scores from the first $ k=2$ principal components which are computed from the
eigenvalues of the correlation matrix of the scaled data

    
```
    ############### PCA manual implementation #########
    Z <- as.matrix(scale(data, center=T, scale=T))
    K <- eigen(cor(Z))
    P <- Z %*% -K$vectors[,1:2]  # scores  = data * loadings
    out <- data.frame(P)
```

$$ P$$ contains the scores of all variables for the first 2 principal
components. This means that the principal components can represent all
variables as a linear combination of weights (**loadings** in jargon). As a
first interpretation, all variables the scores of which are approximatively 0
could be discarded from the principal component. Namely, the principal
component does not need those variables to represent the amount of variance it
is indeed representing. The next question is then, how many components should
I select? A good strategy is to look at the eigenvalues of the correlation
matrix of the original data. All the components with eigenvalue $$ \lt 1 $$ could
be discarded. Another strategy consists in looking at the variance explained
by the principal component, which is strictly related to the eigenvalue. Here
is some code that does the job.

    
``` 
    K$values[1:2]   # first 2 eigenvalues of the correlation matrix 
    v1 = K$values[1]/sum(K$values) # variance explained by pc1
    v2 = K$values[2]/sum(K$values) # variance explained by pc2
```

At the end of the procedure we should have uncorrelated variables, which are
linear combinations of the old variables. They can be ordered by how much
variance they do explain. The first observations that I find misleading are
about using the variables with high variance, because variance equals
information. But if a variable has no high loading on any obtained component,
that means it is basically independent from the other variables in the
analysis. Does this mean it will not contribute to regression? Not
necessarily. Another limitation of PCA consists in the fact that it is
_underspecified_ if we have fewer samples than data points, which is the rule
in genetics. In such a case, every data point will be it's own principal
component. A trick should be used for PCA to work. Its name is matrix
transpose :)

If we really want to be bad with PCA (and I am), I usually think of principal
component scores as _meaningless_. Using PCA's scores is a way to represent
the same data in a different (smaller) dimensional space. This usually allows
the researcher to assign a number to the variable which has no direct relation
with its original value, nor with the other variables. What does that mean
when a variable is considered as a linear combination in e.g. 10 principal
components? What does that mean when it is present in only 2 components? We do
not know.

But the real limitations of PCA are those derived by its design.

## Assumption of linearity

All observed data is a linear combination of a certain basis. Is this always the case? Not at all.


## Assumption on the statistical importance of mean and covariance

PCA uses the eigenvectors of the covariance matrix and it only finds the independent axes of the data under the Gaussian assumption. In the case of non-Gaussian data, PCA simply de-correlates the axes. As a matter of fact, there is no guarantee that the directions of maximum variance will contain good features for discrimination 

## Assumption that large variances have important dynamics  

PCA performs a coordinate rotation that aligns the transformed axes with the directions of maximum variance. That happens every time we compute the scores by multiplying the scaled data by the loadings. But the only case in which principal components with larger variance correspond to interesting dynamics is when the observed data has a high signal-to-noise ratio. That is never the case after data have been cleaned and normalised. So, bioinformaticians, please stop applying PCA on your processed microarray data. It might be a bust!


