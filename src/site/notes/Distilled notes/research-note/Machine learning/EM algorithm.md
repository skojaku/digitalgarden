---
{"dg-publish":true,"permalink":"/distilled-notes/research-note/machine-learning/em-algorithm/","dgHomeLink":true,"dgPassFrontmatter":false}
---


# EM algorithm
updated: 2022-11-15
#machine-learning/classification


The expactation-maximization algorithm is a technique to fit a variety of mixture models such as Gaussian mixture. I'll walk through the key idea and why it works. 

## Problem 

Suppose that you have a set of data samples, each of which is sampled from one of the $K$ probability distributions. You know the functional form of the distributions. The task is to identify  the parameter values as well as which distribution each data sample is generated from. 

## Overview of the EM algorithm 

Let $p_k(x)$ be the probability density function for the $k$th distribution. Given a data sample $x$, the probability that $x$ is generated from the $k$th distribution is given by the posterior distribution, i.e., 
$$
P(k \vert x) = \frac{p(x\vert k)}{p(x)}p(k)=\frac{p(k) p_k(x)}{\sum_{k'}p(k') p_{k'}(x)}.
$$
Probability $P(k \vert x)$ is the probability that $x$ comes from the $k$th distribution. We can then update the parameters $\theta$ of $p(x\vert k)$ with the weighted average of the gradients 
$$
\begin{align}
{\rm d}\theta &= \sum_{i=1}^N\sum_{k=1}^K p(k \vert x) \frac{\partial }{\partial \theta} p(x\vert k), \\
p(k) &= \frac{\sum_{i} q_{ik}}{\sum_{ik} q_{ik}}.
\end{align}
$$
Once we update $\theta$, we effectively update $P(k \vert x)$ since it is parameterized by $\theta$. Thus, we repeat the calculation again. We repeat the rounds of the caluclations until $\theta$ is convered.


## Why it works?

The log-likelihood of the EM algorithm is given by 
$$
J = \sum_{i=1}^N \log \sum_{k=1}^K p(k)  p(x\vert k).
$$
The objective $J$ involves $\log \sum$ which prevents us to derive the analytical form of the gradient with respect to $\theta$. So, we approximate $J$ into another function $J'$ that is convinient to optimize. One such $J'$ can be obtained by using Jensen's inequality, which transforms $\log \sum$ to $\sum \log$, i.e., 
$$
\begin{align}
\log {\mathbb E}_p[f(x)] \geq {\mathbb E}_p[\log f(x)].
\end{align}
$$
if $f$ is a concave function. The intuition behind this is that secant line of a convex function lieves above its function.

![Image](https://pbs.twimg.com/media/E2PR-iaWEAgjP0n.jpg:large)

To apply the Jasen's inequality, we introduce an auxiliary variable $q_{ij}$ that sums to one over $j$, i.e., $\sum_{j}q_{ij} = 1$ for all $i$. Without changing $J$, we introduce $q_{ij}$ to $J$ by 
$$
\begin{align}

J = \sum_{i=1}^N \log \sum_{k=1}^K  q_{ik} \frac{p(k) p(x\vert k)}{q_{ik}}.
\end{align}
$$
Let's apply the Jasen's inequality to $J$:
$$
J \geq J' = \sum_{i=1}^N \sum_{k=1}^K  q_{ik} \log \frac{p(k) p(x\vert k)}{q_{ik}}.
$$
Now, you see that the log of a sum becoems a sum of logs. Also that $J'$ is the lower bound of $J$ so that increasing $J'$ would increase $J$. The equality holds if $\frac{p(k) p(x\vert k)}{q_{ik}}$ is constant, which leads to $q_{ij}$ given by 
$$
q_{ik} = \frac{p(k)p(x \vert k)}{\sum_k p(k)p(x \vert k)}.
$$
Maximizing $J'$ is a constrained maximization problem. We transform the constrained to unconstrained by using Lagrangian, i.e., 

$$
\hat J' = \sum_{i=1}^N \sum_{k=1}^K  q_{ik} \log \frac{p(k) p(x\vert k)}{q_{ik}} + \alpha \left(\sum_{k}p(k) -1\right).
$$
By taking the derivative with respect to $\theta$ and $\alpha$, we have 
$$
\begin{align}
\frac{\partial \hat J'}{\partial \theta} &= \sum_{i=1}^N \sum_{k=1}^K  q_{ik} \frac{\partial}{\partial \theta}\log p(x\vert k) =0\\
\frac{\partial \hat J'}{\partial p(k)} &= \sum_{i=1}^N \sum_{k=1}^K   \frac{q_{ik}}{p(k)} +\alpha=0\\
\frac{\partial \hat J'}{\partial \alpha} &= \sum_{k}p(k) -1 =0
\end{align}
$$
which leads 
$$
\begin{align}
{\rm d}\theta &= \sum_{i=1}^N\sum_{k=1}^K p(k \vert x) \frac{\partial }{\partial \theta} p(x\vert k), \\
p(k) &= \frac{\sum_{i} q_{ik}}{\sum_{ik} q_{ik}}.
\end{align}
$$



