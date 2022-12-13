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


# Neural embedding 
Neural embedding emerges as a powerful alternative to spectral embedding. It is based on neural networks that encode a network into a low dimensional hidden layer. There are two kinds of neural networks, one based on random walks and the other based on convolusion. 

## Based on random walks 
This family of neural embedding adapts a word embedding model for graph embedding. The key idea is to generate an input for a word embedding model (mostly word2vec) by running random walks in networks. The random walker generates a sequence of visited nodes, which is then regarded as "a sentence of nodes" and fed it into the word embedding model. 

- [[DeepWalk\|DeepWalk]] 
- [[Research-note/graph embedding/node2vec\|node2vec]]
- [[LINE\|LINE]] (although it doesn't use random walks explicitly, edge sampling is equivalent to runing a random walk with one step).


## Based on convolusion
- Graph Convolutional network 
- Graph Attention Network 
- GraphSAGE

# Properties 
- [[Research-note/Community detection/Detectability limit of communities\|Detectability limit of communities]]

# Analysis
- [[Research-note/graph embedding/Embedding alignment\|Embedding alignment]]