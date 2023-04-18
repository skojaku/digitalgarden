---
{"dg-publish":true,"permalink":"/literature-notes/papers/kipf-semi-supervised-classification-graph2023/","dgPassFrontmatter":true}
---


**Semi-Supervised Classification with Graph Convolutional Networks**
by Thomas N. Kipf, Max Welling
** (2023)
[Web](https://openreview.net/forum?id=SJU4ayYgl) [Open in zotero]( zotero://select/items/@kipfSemiSupervisedClassificationGraph2023)

**Tags**: 
#literature-note

---

This paper extends the graph convolution network to a layer-wise model for graph neural networks. This extension provides greater flexibility and is the basis of many graph neural networks. 

The core concept behind graph convolutional networks is to convolve the features of a node with those of its neighbours. A node updates its feature variables by taking the feature variables of its neighbours and combining them with its own, followed by a linear transformation and a non-linear activation. By repeating this process, the graph neural network learns a series of linear transformations which transform the original feature variables of the nodes into the final feature variables that reflect the structure of the network.

## Note
- In page three, the authors mentioned about the "renormalization trick". I understand that they normalize the eigenvalues to be upper bounded by one. But not clear why they call "renormalization" yet, and why not other "normalization".
- Batch is not clear to me as well. How do they form a bach given a network?


## Related works 
- [[1312.6203] Spectral Networks and Locally Connected Networks on Graphs](https://arxiv.org/abs/1312.6203)
- [Convolutional Neural Networks on Graphs with Fast Localized Spectral Filtering](https://proceedings.neurips.cc/paper/2016/hash/04df4d434d481c5bb723be1b6df1ee65-Abstract.html)