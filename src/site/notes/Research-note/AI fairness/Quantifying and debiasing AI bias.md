---
{"dg-publish":true,"permalink":"/research-note/ai-fairness/quantifying-and-debiasing-ai-bias/","dgPassFrontmatter":true}
---


# Quantifying and debiasing AI bias
updated: 2023-01-09

#ai-bias 

## Understanding and quantifying bias manifold

Understanding the bias manifold in embedding is instrumental in designing debiasing algorithms. This seminal work demonstrates that word embedding has a linear axis accounting for gender-bias, i.e., bias dimensions.

- [Man is to Computer Programmer as Woman is to Homemaker? Debiasing Word Embeddings](https://papers.nips.cc/paper/2016/hash/a486cd07e4ac3d270571622f4f316ec5-Abstract.html)

Some word emebdding models including Glove and SGNS word2vec embed bias into a linear subspace because the word associations are captured by frequency ratios. 

- The conjecture is provided by [GloVe: Global Vectors for Word Representation - ACL Anthology](https://aclanthology.org/D14-1162/).
- A formal proof is provided by [Towards Understanding Linear Word Analogies - ACL Anthology](https://doi.org/10.18653/v1/P19-1315)

The linearity of bias manifold has led to a metric to quantiy the degree of bias in emebdding. 

- WEAT statistics: [Semantics derived automatically from language corpora contain human-like biases | Science](https://www.science.org/doi/10.1126/science.aal4230)
- Generalized WEAT for multi-categories: [What are the Biases in My Word Embedding? | Proceedings of the 2019 AAAI/ACM Conference on AI, Ethics, and Society](https://dl.acm.org/doi/abs/10.1145/3306618.3314270)

WEAT statistics are common metrics, although they tend to overestimate the bias and not able to capture non-linear bias:

- [Understanding Undesirable Word Embedding Associations](https://arxiv.org/abs/1908.06361)
- [Lipstick on a Pig: Debiasing Methods Cover up Systematic Gender Biases in Word Embeddings But do not Remove Them - ACL Anthology](https://aclanthology.org/N19-1061/)

The picture might look more complex than initially thought, as the bias manifold can be impacted by seemingly inconsequential factors such as word popularity. 

- [dblp: Frequency-based Distortions in Contextualized Word Embeddings.](https://dblp.org/rec/journals/corr/abs-2104-08465.html)
- [Understanding Undesirable Word Embedding Associations - ACL Anthology](https://doi.org/10.18653/v1/P19-1166)

One can quantify the local manifold of bias spanned by the k-nearest neighbors: 

- [Lipstick on a Pig: Debiasing Methods Cover up Systematic Gender Biases in Word Embeddings But do not Remove Them - ACL Anthology](https://aclanthology.org/N19-1061/)

A word takes a *distribution*, instead of a point in space, when the embedding is contextual, as a word representation varies depending on the surrounding words. This calls a new framework to probe bias manifold: 

- [Evaluating the Underlying Gender Bias in Contextualized Word Embeddings - ACL Anthology](https://aclanthology.org/W19-3805/)
- [Measuring Bias in Contextualized Word Representations - ACL Anthology](https://aclanthology.org/W19-3823/)


## Identifying bias

Perturbation analysis can bring out harmful data samples that induce bias: 

- [Understanding the Origins of Bias in Word Embeddings](https://proceedings.mlr.press/v97/brunet19a.html)

Alternatively, one can identify the bias a posteriori from the embedding:

- [What are the Biases in My Word Embedding? | Proceedings of the 2019 AAAI/ACM Conference on AI, Ethics, and Society](https://dl.acm.org/doi/abs/10.1145/3306618.3314270)


## Debiasing 

- Linear projection
	- [Man is to Computer Programmer as Woman is to Homemaker? Debiasing Word Embeddings](https://papers.nips.cc/paper/2016/hash/a486cd07e4ac3d270571622f4f316ec5-Abstract.html)
	- Iterative linear projection: [Null It Out: Guarding Protected Attributes by Iterative Nullspace Projection - ACL Anthology](https://aclanthology.org/2020.acl-main.647/)
- Debiasing by training
	- [Compositional Fairness Constraints for Graph Embeddings](https://arxiv.org/abs/1905.10674)
	- [Censoring Representations with an Adversary — University of Edinburgh Research Explorer](https://www.research.ed.ac.uk/en/publications/censoring-representations-with-an-adversary) 
	- [Learning Gender-Neutral Word Embeddings - ACL Anthology](https://aclanthology.org/D18-1521/)

### Debiasing graph embedding 
- [Compositional Fairness Constraints for Graph Embeddings](https://arxiv.org/abs/1905.10674)
- [Fairwalk: Towards Fair Graph Embedding | IJCAI](https://www.ijcai.org/proceedings/2019/456)
- [CrossWalk: Fairness-Enhanced Node Representation Learning | Proceedings of the AAAI Conference on Artificial Intelligence](https://ojs.aaai.org/index.php/AAAI/article/view/21454)