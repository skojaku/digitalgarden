---
{"dg-publish":true,"permalink":"/research-note/machine-learning/linear-discriminant-analysis/","dgPassFrontmatter":true}
---



# Linear Discriminant Analysis 
#machine-learning/classification

Linear Discrminant Analysis is a dimensionality reduction and classification technique. It is a basis method for many classification algorithms, with a clear geometric interpretation. 


## How it works? 
Suppose that we have $K$-clusters with means $\mu_1,\ldots,\mu_k$ with the same covariance matrix $\Sigma$. This means that each cluster varies along some directions in the space. 

![image](https://drive.google.com/uc?export=view&id=1Yu3UYvYoZeVJNmuYDX1Zfov_KbUaJor7)

LDA first rotates the data and homogenizes the scale so that each cluster has a equi-variance. Then, assign each point to a cluster with the center closest to the point, adjusted by the class popularity.  


## Fisher's disciminant analysis 

Fisher discrminant analysis aims to find a linear discrminant in a different way, which turns out to be the same discriminant as the LDA. An interesting point is that Fisher does not make the assumption of gaussian on data, as opposed to LDA. 

Fisher's idea is that a good subspace should maximize the distance between classes while minimizing the distance within each class, which can be translated into the following problem:
$$
\max_{x} \frac{x^\top B x}{x^\top W w},
$$
where $B$ and $W$ are the between and within class variance matrix defined as 
$$
W = \sum_{k=1}^K \cov(X_k; x_k \in C_k) 
$$
$$
B = \sum_{k=1}^K (\mu_k - \mu)^\top (\mu_k - \mu).
$$

## Logistic regression
Let us revisit the case of two classes and assume that the data follows a gaussian distribution with means $\mu_1$ and $\mu_2$ and variance $\Sigma$. Finding the best dicision boundary with LDA and the logistic regression is essentially the same.

# Reference
- [LDA, Fisher discriminant analysis, and logistic regression](http://www.stat.cmu.edu/~ryantibs/datamining/lectures/21-clas2.pdf)
- [LDA and Fisher discriminant analysis - geometric interpretation](https://towardsdatascience.com/linear-discriminant-analysis-explained-f88be6c1e00b)