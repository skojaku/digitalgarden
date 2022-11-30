---
{"dg-publish":true,"permalink":"/literature-notes/projects/detectability-limit-of-graph-embedding/notes/leaky-eigenvalue-problem/"}
---


 


# Leaky eigenvalue problem

date: 2022-03-21

---

Leaky eigenvalue problem is refers to the problem the increasing likelihood of extreme eigenvalues appeared outside of the range predicted for dense random networks. More sparse the network becomes, more likely to appear are the extreme eigenvalues. 

# References 
- [[Literature notes/papers/archive/Georges arXiv 2017\|Georges arXiv 2017]]
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
