---
{"dg-publish":true,"permalink":"/literature-notes/papers/hamilton-inductive-representation-learning2017/","dgPassFrontmatter":true}
---


**Inductive Representation Learning on Large Graphs**
by Will Hamilton, Zhitao Ying, Jure Leskovec
*Curran Associates, Inc.* (2017)
[Web](https://papers.nips.cc/paper/2017/hash/5dd9db5e033da9c6fb5ba83c7a7ebea9-Abstract.html) [Open in zotero]( zotero://select/items/@hamiltonInductiveRepresentationLearning2017)

**Tags**: 
#literature-note

---

GrpahSAGE extends the idea of graph convolutional network (GCN) by [[Literature notes/papers/@kipfSemiSupervisedClassificationGraph2023\|@kipfSemiSupervisedClassificationGraph2023]]. Two key contributions are (i) to provide a computationally-efficient way to train a large graph neural network and (ii) to set a new paradigm of "inductive" learning of graphs that can generate a representation of new nodes that do not exist in the training network. 

### Algorithm
GraphSAGE consists of three processes: aggregation, concatenation, and linear transformation. For aggregation, feature vectors of immediate neighbors of each node are averaged, pooled, or passed through an LSTM, with pooling and LSTM often yielding the best results. The aggregated vectors are then concatenated before and after the aggregation, with this step being integral to the performance of the system. Finally, the concatenated vectors are filtered and weighted through a linear layer.

## Note
- The original objective function of GraphSAGE is the same as the node2vec objective. The only difference is that while node2vec generates an embedding from scratch, GraphSAGE does so based on a given feature matrix. 