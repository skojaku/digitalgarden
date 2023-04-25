---
{"dg-publish":true,"permalink":"/research-note/network-science/missing-link-prediction/","dgPassFrontmatter":true}
---


# Missing link prediction
updated: 2023-04-01
#network-science/link-prediction


Link prediction is a task that seeks to identify relationships that have not yet been observed in a network. It can be used for a variety of purposes, including building recommendation systems, detecting fraud, and uncovering knowledge. It can also be used to test theories about how networks form, with successful prediction offering insights into the processes that shape their structure.

## Link prediction benchmark
A link prediction algorithm is evaluated based on its ability to predict missing edges that are present but not observed in a given network. The widely-accepted benchmark goes as follows:
1. An algorithm is given a training network with missing edges and is required to provide a prediction score $s_{ij}$ for each pair of nodes $i$ and $j$. The higher the score, the greater the likelihood of an edge existing between those two nodes.
2. Since there are significantly more unconnected nodes than missing edges due to edge sparsity, a subset of unconnected node pairs sampled uniformly at random is used, with the same size as the set of missing edges.
3. The algorithm is deemed to be a successful link prediction algorithm if the score is higher for the missing edges (green in the figure below) than for the unconnected node pairs (red).
4. The overlap of the distributions for the missing edges and unconnected node pairs is commonly quantified by the area under curve (AUC) of the receiving operator characteristics (ROC; right panel).

![](https://camo.githubusercontent.com/95c003777186bbde8c40754f37a56a348cf6fb819bf3a959ad8d99d65a7f71ce/68747470733a2f2f68726e676f6b2e6769746875622e696f2f696d616765732f726f6331302e6a7067)


## Link prediction algorithms 

### Quest for predictive structural variables
A key to a successful link prediction is to find the structural variables that are strongly predictive of edge existence.  Pearhaps the simplest variable is the edge density, with which one predicts that an edge appears between any pair of nodes with the same probability, though this is a crude prediction. 

#### Degree
A more predictive variable is node degree, i.e., number of neighbors in a given network. For a given node pair $(i,j)$, a prediction score is given by
$$
s_{ij} = \log(d_i) + \log(d_j).
$$
Despite its simplicity, degree is surprisingly predictive of edges. Indeed, it sometimes excels more complex link prediction algorithms like graph convolution network and graph attention network. 

- [Residual2Vec: Debiasing graph embedding with random graphs](https://proceedings.neurips.cc/paper/2021/hash/ca9541826e97c4530b07dda2eba0e013-Abstract.html)

Degree is often a strong determinant of many structural variables, and thus, may contribute to their edge predictability.

#### Common neighbors
Common neighbors is a pairwise variable that looks at how many neighbors two nodes have in common, reflecting the local relationship between them. This is a major departure from degree, as it focuses more on the connections between pairs of nodes.

The following structural variables are all based on common neighbors, with difference being the normalization by the degree of common neighbors and the number of neighbors.

- Adamic Adar: 
	- [Friends and neighbors on the Web - ScienceDirect](https://www.sciencedirect.com/science/article/abs/pii/S0378873303000091?via%3Dihub)
- Jaccard index: 
	- [The link prediction problem for social networks | Proceedings of the twelfth international conference on Information and knowledge management](https://dl.acm.org/doi/abs/10.1145/956863.956972?casa_token=aV4JEyGvR9sAAAAA:AaLUWuE0wqD3Uo0Fk7uxPdr_qzswAlo93UhtqoXZst75WqouUDVpUhNsGA9i7fvqXR3dNvWNqJk)
- Resource allocation: 
	- Original paper: [Phys. Rev. E 76, 046115 (2007) - Bipartite network projection and personal recommendation](https://journals.aps.org/pre/abstract/10.1103/PhysRevE.76.046115)
	- Application to link prediction [Predicting missing links via local information | SpringerLink](https://link.springer.com/article/10.1140/epjb/e2009-00335-8)

#### Path 
Path-based variables measure the distance between two nodes in a network by looking at the path between them. This is a generalization of the concept of common neighbors, i.e., two nodes that have common neighbors are connected by the shortest path of length two, the shortest distance for nodes that are not connected in the network.

- Katz
	- The weighted sum of the number of paths of different length
	- About the variable: [A new status index derived from sociometric analysis | SpringerLink](https://link.springer.com/article/10.1007/BF02289026)
	- Application to link prediction: [The link prediction problem for social networks | Proceedings of the twelfth international conference on Information and knowledge management](https://dl.acm.org/doi/abs/10.1145/956863.956972?casa_token=aV4JEyGvR9sAAAAA:AaLUWuE0wqD3Uo0Fk7uxPdr_qzswAlo93UhtqoXZst75WqouUDVpUhNsGA9i7fvqXR3dNvWNqJk)
- Random walk with restart: 
	- The probability that a random walker moves from one node to another, with random events of restarting. 
	- Rooted from PageRank [The anatomy of a large-scale hypertextual Web search engine - ScienceDirect](https://www.sciencedirect.com/science/article/abs/pii/S016975529800110X)
	- Application to link prediction:  [The link prediction problem for social networks | Proceedings of the twelfth international conference on Information and knowledge management](https://dl.acm.org/doi/abs/10.1145/956863.956972?casa_token=aV4JEyGvR9sAAAAA:AaLUWuE0wqD3Uo0Fk7uxPdr_qzswAlo93UhtqoXZst75WqouUDVpUhNsGA9i7fvqXR3dNvWNqJk)
- SimRank:
	- [SimRank | Proceedings of the eighth ACM SIGKDD international conference on Knowledge discovery and data mining](https://dl.acm.org/doi/abs/10.1145/775047.775126?casa_token=2dAvlEOGymQAAAAA:aqRndkwIV1RSqb5TE2cCzX2A2ZWtdR129VPhO7lRIdjxPGy5BcBXklphX031mtXyFh18_u-LljA)
	- (Interpretation is still not clear)
- Local path index
	- A simplified version of Katz index
	- [Phys. Rev. E 80, 046122 (2009) - Similarity index based on local paths for link prediction of complex networks](https://journals.aps.org/pre/abstract/10.1103/PhysRevE.80.046122)
- Local random walk
	- The sum of  the transition probabilities of random walks of different walk length
	- [Link prediction based on local random walk - IOPscience](https://iopscience.iop.org/article/10.1209/0295-5075/89/58007/meta?casa_token=z6kfr7NvfJwAAAAA:xl16SbXlF4oq7-HcR98piZjP5eu4Smo3glqYx82QyW-W1NryrPqsXiZjCEGBy2ZO3cQH79BzswEBufOpIA)

#### Matrix factorization 
- SVD
- PCA
- Laplacian EigenMap

#### Model-based 
- SBM 


## Evaluation metric 

- Issue of AUC-ROC 
- Average precision


## References 

### Benchmark design
- [A Review of Relational Machine Learning for Knowledge Graphs | IEEE Journals & Magazine | IEEE Xplore](https://ieeexplore.ieee.org/document/7358050)
- [A Survey of Link Prediction in Complex Networks | ACM Computing Surveys](https://dl.acm.org/doi/10.1145/3012704)
- [Building a Benchmark for Evaluating Link Prediction Methods | IEEE Conference Publication | IEEE Xplore](https://ieeexplore.ieee.org/document/8508437)
- [Evaluating link prediction methods | SpringerLink](https://link.springer.com/article/10.1007/s10115-014-0789-0)
- [New perspectives and methods in link prediction | Proceedings of the 16th ACM SIGKDD international conference on Knowledge discovery and data mining](https://dl.acm.org/doi/10.1145/1835804.1835837)
- [Link Prediction: Fair and Effective Evaluation | IEEE Conference Publication | IEEE Xplore](https://ieeexplore.ieee.org/abstract/document/6425736)
- [Link prediction techniques, applications, and performance: A survey - ScienceDirect](https://www.sciencedirect.com/science/article/pii/S0378437120300856?casa_token=QOZTSUNd39UAAAAA:Ab2h9oPqyF76CP__jVfg2ad5eeSP8Tat1l6KqUtXSfz9F4vkT19KG__NMjiX1IajHK0BcYIk)
- [Evaluating Link Prediction on Large Graphs](https://upcommons.upc.edu/bitstream/handle/2117/78545/lp_eval.pdf)
### Prediction methods
- Network features:
	- [Link prediction based on local random walk - IOPscience](https://iopscience.iop.org/article/10.1209/0295-5075/89/58007/meta?casa_token=z6kfr7NvfJwAAAAA:xl16SbXlF4oq7-HcR98piZjP5eu4Smo3glqYx82QyW-W1NryrPqsXiZjCEGBy2ZO3cQH79BzswEBufOpIA)
- Ensemble learning:
	- [Stacking models for nearly optimal link prediction in complex networks | PNAS](https://www.pnas.org/doi/10.1073/pnas.1914950117)
- Graph embedding: 
	- [[1711.08267] GraphGAN: Graph Representation Learning with Generative Adversarial Nets](https://arxiv.org/abs/1711.08267)
	- [Link Prediction Based on Graph Neural Networks](https://proceedings.neurips.cc/paper/2018/hash/53f0d7c537d99b3824f0f99d62ea2428-Abstract.html)