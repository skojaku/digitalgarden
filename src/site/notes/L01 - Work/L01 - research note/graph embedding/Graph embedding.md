---
{"dg-publish":true,"permalink":"/l01-work/l01-research-note/graph-embedding/graph-embedding/","dgPassFrontmatter":true}
---

#network-science/graph-embedding 

Graph embedding maps a network into a vector space, which let us explore the relationships of nodes using a simple vector operation, or feed them into machine learning algorithms. 

# Spectral embedding 
Spectral embedding is a technique that generates an embedding by decomposing a matrix that represents a network. This matrix can take various forms, such as an adjacency matrix, a Laplacian matrix, or a random walk transition matrix. Spectral embedding is rooted in the principles of linear algebra and its properties have been extensively studied using tools from random matrix theory. 

- **Methods**
	- Laplacian EigenMap
	- Diffusion Map
	- [Modularity embedding](https://journals.aps.org/prl/abstract/10.1103/PhysRevLett.108.188701)
	- [Non-backtracking embedding](https://www.pnas.org/doi/10.1073/pnas.1312486110)
	- [Flow-based embedding](https://arxiv.org/abs/1308.6494)

# Neural graph embedding 

Neural graph embedding is a technique that utilizes neural networks. It can be traced back to two distinct branches: one originating from neural networks used in natural language processing, and the other from those used in image processing.
## Embedding based on language models 

This branch originates from neural language models used in natural language processing. Language models are designed to analyze text consisting of sequential characters' data. Although networks are not inherently sequential, language models can be applied to network data by transforming a network into a sequence of nodes and edges, such as using random walks.

- [LINE | Proceedings of the 24th International Conference on World Wide Web](https://dl.acm.org/doi/abs/10.1145/2736277.2741093?casa_token=nA3KfYzUUcEAAAAA:ljXUQW7C2uKdcT7lQidqYW2rrw9PN4vEiFdnUbxD4DClyDynWswU6qk-RKY2eY1vICQ_4b-Wmt8)
- [DeepWalk | Proceedings of the 20th ACM SIGKDD international conference on Knowledge discovery and data mining](https://dl.acm.org/doi/abs/10.1145/2623330.2623732?casa_token=qlrZF1AktOMAAAAA:j_slF0ga856XY0EdBnW04A-B3-YXBzBgJscNonHrITLcN2htIVYK8OYdJEx8Uw4GIi8FTewIFnE)
- [node2vec | Proceedings of the 22nd ACM SIGKDD International Conference on Knowledge Discovery and Data Mining](https://dl.acm.org/doi/abs/10.1145/2939672.2939754?casa_token=6E0ducYusagAAAAA:s_6NCxSk2ZoUTJl2zyUz1S0gIXuw2ewTHTbU_rVVSHgQPekFaLKetrZBQYpUW_KxfrT0rrd9Tj0)
- See also my note on [[L01 - Work/L01 - research note/graph embedding/node2vec\|node2vec]]

## Embedding based on image processing

Graph convolution is a technique that originated from image processing. An image is represented as a regular graph, in which each pixel is represented as a node and connected to adjacent pixels. A node has RGB colors as the feature vector. The purpose of graph convolution is to use a basic operation called convolution to identify edges, shapes, and objects.

- [[1312.6203] Spectral Networks and Locally Connected Networks on Graphs](https://arxiv.org/abs/1312.6203)

The concept of convolution has been extended to irregular graphs, such as social networks. This extension allows for applying convolutional neural networks on graphs with fast localized spectral filtering. 

- [Convolutional Neural Networks on Graphs with Fast Localized Spectral Filtering](https://proceedings.neurips.cc/paper/2016/hash/04df4d434d481c5bb723be1b6df1ee65-Abstract.html)
- [Semi-Supervised Classification with Graph Convolutional Networks | OpenReview](https://openreview.net/forum?id=SJU4ayYgl). 

In addition to graph convolution, different aggregation strategies can be adopted, including concatenation and pooling. 

- [Inductive Representation Learning on Large Graphs](https://proceedings.neurips.cc/paper_files/paper/2017/hash/5dd9db5e033da9c6fb5ba83c7a7ebea9-Abstract.html). See also [[@hamiltonInductiveRepresentationLearning2017\|@hamiltonInductiveRepresentationLearning2017]]. 

For scalable computation, mini-batching networks can be used. This approach is discussed in the paper "Cluster-GCN".

- [Cluster-GCN | Proceedings of the 25th ACM SIGKDD International Conference on Knowledge Discovery & Data Mining](https://dl.acm.org/doi/abs/10.1145/3292500.3330925)


# Modeling networks with embedding 
 
Modeling the growth of networks by a geometric branching process, in which a parent node is split into multiple offspring that inherit the properties of the parent, which can regenerate numerous ubiquitous network features, including degree heterogeneity and stable community structure. It is an inverse transformation of geometric renormalization. 

- [Scaling up real networks by geometric branching growth | PNAS](https://www.pnas.org/doi/10.1073/pnas.2018994118)

# References
- [Introduction to Graph Machine Learning](https://huggingface.co/blog/intro-graphml)

# Properties 
- [[L01 - Work/L01 - research note/Community detection/Detectability limit of communities\|Detectability limit of communities]]

# Analysis
- [[L01 - Work/L01 - research note/graph embedding/Embedding alignment\|Embedding alignment]]