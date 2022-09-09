---
{"dg-publish":true,"permalink":"/research-note/graph-embedding/graph-embedding/","dgHomeLink":true,"dgPassFrontmatter":false}
---


Graph embedding maps a network into a vector space, which let us explore the relationships of nodes using a simple vector operation, or feed them into machine learning algorithms. 


# Spectral embedding 

Spectral embedding produces an embedding by factorizing a matrix representing a network. The matrix can be an adjacency matrix, laplacian matrix, random walk transition matrix, and etc. Spectral embedding is grounded on linear algebra, and it's properties are well explored using tools from random matrix theory. In many ways, we know a lot about the capacity of spectral embedding. 

- **Methods**
	- Laplacian EigenMap
	- Diffusion Map
	- [Modularity embedding](https://journals.aps.org/prl/abstract/10.1103/PhysRevLett.108.188701)
	- [Non-backtracking embedding](https://www.pnas.org/doi/10.1073/pnas.1312486110)
	- [[Flow-based embedding|Flow-based embedding]](https://arxiv.org/abs/1308.6494)

# Neural embedding 

Neural embedding emerges as a powerful alternative to spectral embedding. It is based on neural networks that encode a network into a low dimensional hidden layer. There are two kinds of neural networks, one based on random walks and the other based on convolusion. 

## Based on random walks 
This family of neural embedding adapts a word embedding model for graph embedding. The key idea is to generate an input for a word embedding model (mostly word2vec) by running random walks in networks. The random walker generates a sequence of visited nodes, which is then regarded as "a sentence of nodes" and fed it into the word embedding model. 

- [[DeepWalk|DeepWalk]] 
- [[research-note/graph embedding/node2vec|node2vec]]
- [[LINE|LINE]] (although it doesn't use random walks explicitly, edge sampling is equivalent to runing a random walk with one step).


## Based on convolusion
- Graph Convolusional network 
- Graph Attention Network 
- GraphSAGE

# Graph embedding for community detection 

Graph embedding can be used to identify communities in networks. By embedding a network into a vector space, we have a geometry of nodes, in which communities are projected into clusters. 

### Detectability limit 

Algorithms may not be able to find communities even if communities are interally denser than externally. This is because algorithms may find some random communies that are also internally denser than externally and equally as good as the ground-truth communities. Detectability limit refers to the maximum level of "noise" above which any algorithm fails.

The detectability limit depends on the sparsity of networks. If the given network is dense network, there exists an algorithm that can find communities if they are internally denser than externally (i.e., communities exist). 

**dense regime**: Degree increases with respect to the number of nodes
- Larger window size is better [[papers/literature note/@zhangConsistencyRandomwalkBased2021|@zhangConsistencyRandomwalkBased2021]] [[papers/literature note/@barotCommunityDetectionUsing2021|@barotCommunityDetectionUsing2021]]
- Non-backtracking walks improve the detectability limit of graph embedding [[papers/literature note/@barotCommunityDetectionUsing2021|@barotCommunityDetectionUsing2021]]
- Detectability limit for communities of different sizes [[papers/literature note/@chenUniversalPhaseTransition2015|@chenUniversalPhaseTransition2015]]
- Detectability limit of networks with communities of different sizes and internal strucure [[papers/literature note/@chenPhaseTransitionsSpectral2014|@chenPhaseTransitionsSpectral2014]]

**sparse regime**: Degree is fixed constant. 
- [[papers/archive/Nadakuditi PRL 2012|Nadakuditi PRL 2012]]


The detectability limit also depends on the heterogeneity in degree and community sizes. To my surprise, heterogeneity makes it easy for algorithms to identify communities.

- Ill-defined communities are more detectable than well-defined communites [[papers/literature note/@radicchiParadoxCommunityDetection2013|@radicchiParadoxCommunityDetection2013]]
- Degree heterogeneity accerates the ability to detect communities (for the modularity maximization) [[papers/literature note/@radicchiDetectabilityCommunitiesHeterogeneous2013|@radicchiDetectabilityCommunitiesHeterogeneous2013]]
- (*dense networks*) Detectability limit of networks with communities of different sizes and internal strucure [[papers/literature note/@chenPhaseTransitionsSpectral2014|@chenPhaseTransitionsSpectral2014]]
-  (*dense networks*) Detectability limit for communities of different sizes [[papers/literature note/@chenUniversalPhaseTransition2015|@chenUniversalPhaseTransition2015]]

Most study focus on the detectability limit of spectral embedding. What about nueral embedding?

-  The detectability limit of the GNN is imposed by the architecture, and the accuracy of performance in detectable regime is attributed to backpropagation [[papers/literature note/@kawamotoMeanfieldTheoryGraph2018|@kawamotoMeanfieldTheoryGraph2018]].  