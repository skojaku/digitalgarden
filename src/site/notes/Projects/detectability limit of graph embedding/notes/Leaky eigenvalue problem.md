---
{"dg-publish":true,"permalink":"/projects/detectability-limit-of-graph-embedding/notes/leaky-eigenvalue-problem/","dgPassFrontmatter":true}
---


 


# Leaky eigenvalue problem

date: 2022-03-21

---

A cornerstone of the random matrix is [Wigner's semi circle law](https://en.wikipedia.org/wiki/Wigner_semicircle_distribution), which explains that the eigenvalues of a random matrix are bounded. This law, however, breaks if the random mtarix is extremely sparse, a problem called the leaky eigenvalue problem.

# References 
- [[Papers/archive/Georges arXiv 2017\|Georges arXiv 2017]]
- http://helper.ipam.ucla.edu/publications/qlaws3/qlaws3_14643.pdf

### Range of extreme eigenvalues


$$\lambda_1(A) = 
\left\{
\begin{array}{ll}
(\log n)^{1/2} & \text{if}\; d\ll (\log n)^{1/2},\\
d & \text{if}\; d\gg (\log n)^{1/2}.
\end{array}
\right. 
$$
$$\lambda_2(A) = 
\left\{
\begin{array}{ll}
(\log n)^{1/2} & \text{if}\; d\ll (\log n)^{1/2},\\
2\sqrt{d} & \text{if}\; d\gg (\log n)^{4}.
\end{array}
\right. 
$$
Because the spectrum radius expands if d is extremely small, the modularity embedding falls short in community detection for sparse networks.
