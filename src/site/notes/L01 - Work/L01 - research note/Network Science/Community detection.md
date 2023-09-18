---
{"dg-publish":true,"permalink":"/l01-work/l01-research-note/network-science/community-detection/","dgPassFrontmatter":true}
---


## Graph cut 

Graph cut is a problem of finding a minimal set of edges whose removal breaks a connected component into multiple disconnected components. Finding such a minimal edge set is often an NP-hard combinatorial problem. However, it is possible to find a fairly good cut by relaxing the discrete combinatorial problem into a spectral decomposition problem. 

- [A tutorial on spectral clustering | SpringerLink](https://link.springer.com/article/10.1007/s11222-007-9033-z)

## Modularity 

Modularity introduces the idea that communities must be denser than *random* connections (i.e. a null model). The introduction of null models is a major departure from graph cuts, which may find communities sparser than random connections. 

- [[cond-mat/0308217] Finding and evaluating community structure in networks](https://arxiv.org/abs/cond-mat/0308217)
- [Phys. Rev. E 74, 036104 (2006) - Finding community structure in networks using the eigenvectors of matrices](https://journals.aps.org/pre/abstract/10.1103/PhysRevE.74.036104)
- [Modularity and community structure in networks | PNAS](https://www.pnas.org/doi/10.1073/pnas.0601602103)

We can introduce domain knowledge about random connections. For instance, if a network is a railroad network, the random network must be a planner graph with no edges crossing. There are many variants of modularity combined with different null models:
- [Uncovering space-independent communities in spatial networks | PNAS](https://www.pnas.org/doi/full/10.1073/pnas.1018962108)

Limitation: 
- [Resolution limit in community detection | PNAS](https://www.pnas.org/doi/full/10.1073/pnas.0605965104)
- [Phys. Rev. E 81, 046106 (2010) - Performance of modularity maximization in practical contexts](https://journals.aps.org/pre/abstract/10.1103/PhysRevE.81.046106)
- [Tiago de Paula Peixoto — Blog](https://skewed.de/tiago/blog/modularity-harmful)

## Embedding + Clustering 


## Stochastic Block model 
