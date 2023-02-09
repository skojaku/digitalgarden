---
{"dg-publish":true,"permalink":"/research-note/network-science/configuration-model/","dgPassFrontmatter":true}
---


# Configuration model
updated: 2022-11-21
#network-science/random-networks

The configuration model is widely used as a baseline model to assess the significance of patterns observed in empirical networks.  It is a model of random networks that preserves a critical characteristic of networks, i.e., node degree. 

## Specification of configuration models
An often underappreciated fact is that there are multiple specifications of the configuration model and that the decision to choose which specification results in a profound impact on the final results. 

- [Configuring Random Graph Models with Fixed Degree Sequences | SIAM Review](https://epubs.siam.org/doi/10.1137/16M1087175)


### Unweighted networks

The simplest form of the configuration model is **the Chung-Lu model**:

[Connected Components in Random Graphs with Given Expected Degree Sequences | SpringerLink](https://link.springer.com/article/10.1007/PL00012580)

which samples two nodes independently with probability proportional to the degree and places a link between them. It allows multiple edges and self-loops, but the likelihood of the events is very negligible for large networks.

Although the chances are small, sometimes we want to prevent self-loops and multiple edges. Furthermore,  the Chung-Lu model is *not maximally random*. A more rigorous model preserving the degree sequence is the **enhanced configuration model**:

- [Phys. Rev. Lett. 102, 038701 (2009) - Generalized Bose-Fermi Statistics and Structural Correlations in Weighted Networks](https://journals.aps.org/prl/abstract/10.1103/PhysRevLett.102.038701)
- [Enhanced reconstruction of weighted networks from strengths and degrees - IOPscience](https://iopscience.iop.org/article/10.1088/1367-2630/16/4/043022)

The enhanced configuration model is computationally expensive, which is one big reason people like the Chung-Lu model over the enhanced configuration model. A follow-up paper mitigates the computation cost by using an efficient quadratic programming solver:

- [Fast and scalable likelihood maximization for Exponential Random Graph Models with local constraints | Scientific Reports](https://www.nature.com/articles/s41598-021-93830-4)

Yet, in my opinion, the computational cost is fundamentally the same, which limits the use of the enhanced configuration model for large networks (although I like the idea). 

### Weighted networks 

A naive extension of the configuration model to weighted networks is to regard an edge with weight $w$ as $w$ edges of weight one. This heuristics is cheap and preserved the weighted degree (or strength). However, it does not preserve the number of neighbors of each node, or simply degree.

The enhanced configuration model can preserve the node strengths.

- [Phys. Rev. Lett. 102, 038701 (2009) - Generalized Bose-Fermi Statistics and Structural Correlations in Weighted Networks](https://journals.aps.org/prl/abstract/10.1103/PhysRevLett.102.038701)
- [Enhanced reconstruction of weighted networks from strengths and degrees - IOPscience](https://iopscience.iop.org/article/10.1088/1367-2630/16/4/043022)

### Directed acyclic graph (DAG)

Directed acyclic graph is a network without loops. In DAG, each edge is directed and always pointing from a higher to lower levels of a hirarchy. A configuration model that repsects this constraint is proposed by 

- [Phys. Rev. E 80, 046110 (2009) - Random graph models for directed acyclic networks](https://journals.aps.org/pre/abstract/10.1103/PhysRevE.80.046110)

### Correlation networks

Correlation networks are a type of weighted networks, where weights represent correlations. Correlation networks should be treated with caution, because correlations are not independent of each other. Two nodes are strongly correlated even without any dydiac relationships if they are correlated with other nodes in a system. The enhanced configuration model does not respect the mutual correlations of correlations, and its naive application to correlation networks may result in poor understanding and prediction. 

The configuration model for correlation data builds on the principle of maximum entropy; it conside a maximally random correlation data constrained on the weighted degree of each node in the given correlation network. 

- [Phys. Rev. E 98, 012312 (2018) - Configuration model for correlation matrices preserving the node strength](https://journals.aps.org/pre/abstract/10.1103/PhysRevE.98.012312)

There are many other null models for correlation networks, apart from the configuration model:

- [Phys. Rev. X 5, 021006 (2015) - Community Detection for Correlation Matrices](https://journals.aps.org/prx/abstract/10.1103/PhysRevX.5.021006)


## Algorithms

### Unweighted networks
Simulating the configuration model appears to be expensive, as it is a collection of $N(N-1)/2$ binary variables representing the presence of edges. Luckly, we have an efficient algorithm that runs linear with respect to the number of edges.

- [Efficient Generation of Networks with Given Expected Degrees | SpringerLink](https://link.springer.com/chapter/10.1007/978-3-642-21286-4_10)

If multiedges are allowed, an easy and cheap method is the Chung-Lu model.

- [Connected Components in Random Graphs with Given Expected Degree Sequences | SpringerLink](https://link.springer.com/article/10.1007/PL00012580)

### Weighted and directed networks

The enhanced configuration model can handle weighted and directed networks. A fast library for the enhanced configuration model is proposed by 

- [Fast and scalable likelihood maximization for Exponential Random Graph Models with local constraints | Scientific Reports](https://www.nature.com/articles/s41598-021-93830-4)

### Directed Acyclic Graph

If the network is DAG, we can utilize the ordering of nodes to efficiently generate the configuration model:

- [Phys. Rev. E 80, 046110 (2009) - Random graph models for directed acyclic networks](https://journals.aps.org/pre/abstract/10.1103/PhysRevE.80.046110)