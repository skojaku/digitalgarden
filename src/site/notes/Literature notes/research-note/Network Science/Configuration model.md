---
{"dg-publish":true,"permalink":"/literature-notes/research-note/network-science/configuration-model/","dgHomeLink":true,"dgPassFrontmatter":false}
---


# Configuration model
updated: 2022-11-21
#network-science/random-networks

The configuration model is widely used as a baseline model to assess the significance of patterns observed in empirical networks.  It is a model of random networks that preserves a fundamental characteristics of networks, node degree. 

## Specification of configuration models
An often appreciated fact is that there are multiple specificications of the configuration model, and that the decision to choose which specification results in a profound impact on the final results. 

### Unweighted networks

- [Configuring Random Graph Models with Fixed Degree Sequences | SIAM Review](https://epubs.siam.org/doi/10.1137/16M1087175)


### Weighted networks 

A naive extention of the configuration model to weighted networks is to regard an edge with weight $w$ as $w$ edges of weight one. This heuristics is cheap and preserved the weighted degree (or strength). However, it does not preserve the number of neighbor of each node, or simply degree. This is a critical problem as degree is a fundamental determinant of network structure. 

The enhanced configuration model is an extention of the configuration model for unweighted networks. It formulates the configuration model as a canonical model constrained by degree. To respect to edge weights, it adds additional constraints on the weighted degree.

- [Phys. Rev. Lett. 102, 038701 (2009) - Generalized Bose-Fermi Statistics and Structural Correlations in Weighted Networks](https://journals.aps.org/prl/abstract/10.1103/PhysRevLett.102.038701)
- [Enhanced reconstruction of weighted networks from strengths and degrees - IOPscience](https://iopscience.iop.org/article/10.1088/1367-2630/16/4/043022)

### Directed acyclic graph (DAG)

Directed acyclic graph is networks without loops. In DAG, each edge is directed and always pointing from a higher to lower levels of a hirarchy. A configuration model that repsects this constraint is proposed by 

- [Phys. Rev. E 80, 046110 (2009) - Random graph models for directed acyclic networks](https://journals.aps.org/pre/abstract/10.1103/PhysRevE.80.046110)

### Correlation networks

Correlation networks are a type of weighted networks, where weights represent correlations. Correlation networks should be treated with caution, because correlations are not independent of each other. Two nodes are strongly correlated even without any dydiac relationships if they are correlated with other nodes in a system. The enhanced configuration model does not respect the mutual correlations of correlations, and its naive application to correlation networks may result in poor understanding and prediction. 

The configuration model for correlation data builds on the principle of maximum entropy; it conside a maximally random correlation data constrained on the weighted degree of each node in the given correlation network. 

- [Phys. Rev. E 98, 012312 (2018) - Configuration model for correlation matrices preserving the node strength](https://journals.aps.org/pre/abstract/10.1103/PhysRevE.98.012312)

There are many other null models for correlation networks, apart from the configuration model:

- [Phys. Rev. X 5, 021006 (2015) - Community Detection for Correlation Matrices](https://journals.aps.org/prx/abstract/10.1103/PhysRevX.5.021006)


## Computing the configuration model

### Unweighted networks
Simulating the configuration model appears to be expensive, as it is a collection of $N(N-1)/2$ binary variables representing the presence of edges. Luckly, we have an efficient algorithm that runs linear with respect to the number of edges.

- [Efficient Generation of Networks with Given Expected Degrees | SpringerLink](https://link.springer.com/chapter/10.1007/978-3-642-21286-4_10)

If multiedges are allowed, an easy and cheap method is so-called Chung-Lu model.

- [Connected Components in Random Graphs with Given Expected Degree Sequences | SpringerLink](https://link.springer.com/article/10.1007/PL00012580)

