---
{"dg-publish":true,"permalink":"/research-note/graph-embedding/graph-embedding/","dgPassFrontmatter":true}
---

#network-science/graph-embedding 

Graph embedding maps a network into a vector space, which let us explore the relationships of nodes using a simple vector operation, or feed them into machine learning algorithms. 


# Spectral embedding 
Spectral embedding produces an embedding by factorizing a matrix representing a network. The matrix can be an adjacency matrix, laplacian matrix, random walk transition matrix, and etc. Spectral embedding is grounded on linear algebra, and it's properties are well explored using tools from random matrix theory. In many ways, we know a lot about the capacity of spectral embedding. 

- **Methods**
	- Laplacian EigenMap
	- Diffusion Map
	- [Modularity embedding](https://journals.aps.org/prl/abstract/10.1103/PhysRevLett.108.188701)
	- [Non-backtracking embedding](https://www.pnas.org/doi/10.1073/pnas.1312486110)
	- [[Flow-based embedding\|Flow-based embedding]](https://arxiv.org/abs/1308.6494)


# Graph neural networks

Graph neural networks adopt artificial neural networks to learn patterns in network structure. Graph neural networks serve as powerful alternatives to classical spectral methods, and their advances have been fueled by the success of neural networks in image and text processing. 

## Key idea 
Let's focus on node embedding. Neural networks learn a projection of nodes onto a vector space, in which two nodes that are "close" in the original network are also close to each other in the embedding space.  We teach neural networks through examples, where each example is formed by a pair of nodes that are "close" to each other in the given network, which are then mapped to be close to each other in the embedding space. There are an innumerable number of variants in graph neural networks depending on how we *sample* the training examples, and whether or not a *convolution* mechanism is used to create an embedding. 

### Sampling nodes from networks. 
A simple way to generate training examples is to sample from the edge list, meaning that  each example is formed by nodes connected directly by an edge. In social networks, for example, if my friends and I have formed a bond, neural networks should learn from the friendship tie and project us to be close to each other in the embedding space. A prominent graph neural network that learns from the edge list is *LINE*. 

- [LINE | Proceedings of the 24th International Conference on World Wide Web](https://dl.acm.org/doi/abs/10.1145/2736277.2741093?casa_token=nA3KfYzUUcEAAAAA:ljXUQW7C2uKdcT7lQidqYW2rrw9PN4vEiFdnUbxD4DClyDynWswU6qk-RKY2eY1vICQ_4b-Wmt8)

This paper proposes a new version of LINE that learns *the second-order proximity*. This means that two nodes are considered to be similar if they have many shared neighbors. This concept is especially helpful when trying to find nodes that have a similar structural role (e.g. core of core-periphery structure). To further build upon this concept, random walks are used to sample the neighbors of neighbors and their neighbors, and so on, in order to learn a higher-order proximity.

- [DeepWalk | Proceedings of the 20th ACM SIGKDD international conference on Knowledge discovery and data mining](https://dl.acm.org/doi/abs/10.1145/2623330.2623732?casa_token=qlrZF1AktOMAAAAA:j_slF0ga856XY0EdBnW04A-B3-YXBzBgJscNonHrITLcN2htIVYK8OYdJEx8Uw4GIi8FTewIFnE)
- [node2vec | Proceedings of the 22nd ACM SIGKDD International Conference on Knowledge Discovery and Data Mining](https://dl.acm.org/doi/abs/10.1145/2939672.2939754?casa_token=6E0ducYusagAAAAA:s_6NCxSk2ZoUTJl2zyUz1S0gIXuw2ewTHTbU_rVVSHgQPekFaLKetrZBQYpUW_KxfrT0rrd9Tj0)
- See also my note on [[Research-note/graph embedding/node2vec\|node2vec]]

### Graph convolution
Graph convolution is a technique derived from image processing, in which a pixel is represented as a node with its RGB colors as the feature vector and is connected to other nodes by adjacent pixels. This technique uses convolution, a basic operation to identify edges, shapes, and objects.

- [[1312.6203] Spectral Networks and Locally Connected Networks on Graphs](https://arxiv.org/abs/1312.6203)

In the context of graph learning, one extends the idea of convolution to irregular graphs like social networks. 

- [Convolutional Neural Networks on Graphs with Fast Localized Spectral Filtering](https://proceedings.neurips.cc/paper/2016/hash/04df4d434d481c5bb723be1b6df1ee65-Abstract.html)
- [Semi-Supervised Classification with Graph Convolutional Networks | OpenReview](https://openreview.net/forum?id=SJU4ayYgl). See also my note [[Literature notes/papers/@kipfSemiSupervisedClassificationGraph2023\|@kipfSemiSupervisedClassificationGraph2023]]

Additionally, one can adopt different aggregation strategies such as concatenation and pooling:

- [Inductive Representation Learning on Large Graphs](https://proceedings.neurips.cc/paper_files/paper/2017/hash/5dd9db5e033da9c6fb5ba83c7a7ebea9-Abstract.html). See also [[Literature notes/papers/@hamiltonInductiveRepresentationLearning2017\|@hamiltonInductiveRepresentationLearning2017]]. 


- Spectral Graph convolution 
- Graph Convolutional network 
- Graph Attention Network 
- GraphSAG

# References
- [Introduction to Graph Machine Learning](https://huggingface.co/blog/intro-graphml)

# Properties 
- [[Research-note/Community detection/Detectability limit of communities\|Detectability limit of communities]]

# Analysis
- [[Research-note/graph embedding/Embedding alignment\|Embedding alignment]]