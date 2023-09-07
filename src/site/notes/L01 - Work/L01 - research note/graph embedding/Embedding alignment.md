---
{"dg-publish":true,"permalink":"/l01-work/l01-research-note/graph-embedding/embedding-alignment/","dgPassFrontmatter":true}
---


# Embedding alignment
updated: 2022-12-13

Embedding alignment puts together two independent embeddings into the same space, which enables comparison and knowledge transfer. For instance, one can create a time series of historical word embedding by aligning embeddings generated across different years. 

- [Diachronic Word Embeddings Reveal Statistical Laws of Semantic Change - ACL Anthology](https://aclanthology.org/P16-1141/)

A simple approach to enable this is to find a *rotation* that aligns one embedding to the other as much as possible. This approach is called the orthogonal Procrustes. 

[Orthogonal Procrustes problem - Wikipedia](https://en.wikipedia.org/wiki/Orthogonal_Procrustes_problem)

For other methods, see [Closed Form Word Embedding Alignment](https://arxiv.org/abs/1806.01330).

