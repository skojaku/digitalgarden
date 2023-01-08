---
{"dg-publish":true,"permalink":"/misc/papers/archive/ethayarajh-acl-2019/","dgPassFrontmatter":true}
---



# Understanding undesirable word embedding associations


Ethayarajh, K., Duvenaud, D., & Hirst, G. (2019). Understanding Undesirable Word Embedding Associations. _Proceedings of the 57th Annual Meeting of the Association for Computational Linguistics_, 1696–1705. https://doi.org/10.18653/v1/P19-1166

#ai-bias

---
- There is a lack of understanding about how to measure and remove biases from word embeddings
- A method called subspace projection can be used to debias word embeddings and is equivalent to training on an unbiased corpus under certain conditions.
-  he most commonly used association test for word embeddings, WEAT, overestimates bias
- A new measure of an association called the relational inner product association (RIPA) has been developed using subspace projection.
- Skipgram with negative sampling (SGNS) does not generally make words more gendered than they are in the training corpus, but it can amplify the gender association for stereotyped words.


