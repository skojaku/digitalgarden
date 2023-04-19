---
{"dg-publish":true,"permalink":"/misc/jobs/interviews/binghamton/statistical-mechanics-of-community-detection/","dgPassFrontmatter":true}
---


# Statistical mechanics of community detection
updated: 2023-01-20

Spin glass is a model that explains the disorder magnetization state of matter, which can be represented as a network, where a spin is represented as a node, and edges represent the interactions between spins. The model can be applied to community detection, where a stable state gives us the community structure in networks. 

A seminal work characterizes a network as an Ising model:

- [Phys. Rev. E 74, 016110 (2006) - Statistical mechanics of community detection](https://journals.aps.org/pre/abstract/10.1103/PhysRevE.74.016110)

See also: 

- [When are networks truly modular? - ScienceDirect](https://www.sciencedirect.com/science/article/abs/pii/S0167278906003678)

Modularity maximization, by far well-known community detection, is also grounded on the Ising model:

- [Modularity and community structure in networks | PNAS](https://www.pnas.org/doi/10.1073/pnas.0601602103)

This spurs various variants of Ising models with different null models: 
- [Uncovering space-independent communities in spatial networks | PNAS](https://www.pnas.org/doi/full/10.1073/pnas.1018962108)
- [Phys. Rev. X 5, 021006 (2015) - Community Detection for Correlation Matrices](https://journals.aps.org/prx/abstract/10.1103/PhysRevX.5.021006)
- [Constructing networks by filtering correlation matrices: a null model approach | Proceedings of the Royal Society A: Mathematical, Physical and Engineering Sciences](https://royalsocietypublishing.org/doi/full/10.1098/rspa.2019.0578)
- [Community detection in directed acyclic graphs | SpringerLink](https://link.springer.com/article/10.1140/epjb/e2015-60226-y)
- [[0801.1647] Extending the definition of modularity to directed graphs with overlapping communities](https://arxiv.org/abs/0801.1647)

The modularity touches various crucial features of networks. The spectrum of the modularity matrix, for instance, is related to the community structure:

- [Phys. Rev. E 74, 036104 (2006) - Finding community structure in networks using the eigenvectors of matrices](https://journals.aps.org/pre/abstract/10.1103/PhysRevE.74.036104)

as well as the information-theoretic limit of community detectability: 

- [Phys. Rev. Lett. 108, 188701 (2012) - Graph Spectra and the Detectability of Community Structure in Networks](https://journals.aps.org/prl/abstract/10.1103/PhysRevLett.108.188701)

***Trivia***:  The eigenvectors and eigenvalues of the modularity matrix are identical to those of the adjacency matrix, except the trivial eigenvector is proportional to the degree of centrality. 

