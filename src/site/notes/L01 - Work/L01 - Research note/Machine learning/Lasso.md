---
{"dg-publish":true,"permalink":"/l01-work/l01-research-note/machine-learning/lasso/","dgPassFrontmatter":true}
---


# Lasso
updated: 2023-02-06
#machine-learning/lasso


Lasso in machine learning is a *model regularization* to learn sparse models and sparse data representations through $L1$ regularization, i.e., 

$$
\hat L(X;w) = L(X;w) + \lambda |w|_1
$$
where $L(X;w)$ is the objective for a model with parameters $\theta$ and data $X$, and $\hat L$ is the regularized objective. Parameter $\lambda$ is the lasso penalty, which controls the sparsity of the model. 

Lasso stands for the least absolute shrinkage and selection operator proposed in 1996 by Robert Tibshirani. 

-  [Regression Shrinkage and Selection via the Lasso on JSTOR](https://www.jstor.org/stable/2346178#metadata_info_tab_contents)

Lasso quickly becomes one of the fundamental methods used in a variety of machine learning methods. 




## Why Lasso?

- Preventing overfitting 
- Colinearity problem
- Interpretability

![](https://user-images.githubusercontent.com/18026375/216966455-be931c3c-98e9-4d26-9fca-732c8ed3174c.png)

![](https://user-images.githubusercontent.com/18026375/216967343-af768385-bafe-4507-88b7-ca226f6dc740.png)

## Why it works?

- Intuition
- Lasso from laglagian perspective
- Gradient

## Adaptive lasso

- Bias and variance 

## Lasso in neural networks

- LassoNet

## Sparse coding
- Sparse PCA (dictionary & atom)

## References 
- [“Lasso & Ridge Regression” in 200 Words - Data Science](https://thaddeus-segura.com/lasso-ridge/)