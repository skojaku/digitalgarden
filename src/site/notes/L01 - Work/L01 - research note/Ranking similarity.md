---
{"dg-publish":true,"permalink":"/l01-work/l01-research-note/ranking-similarity/","dgPassFrontmatter":true}
---


# Ranking similarity 
updated: 2022-11-25
#machine-learning/metrics

How similar are the two rankings? Answering this question leads to a variety of ranking similarity metrics. 

## Ranking correlation 

We can measure the similarity between two entities using correlation. For example, if the entities have two variables representing their positions in two rankings, the correlation between the variables can be used to quantify the similarity.

- [Spearman's rank correlation coefficient - Wikipedia](https://en.wikipedia.org/wiki/Spearman%27s_rank_correlation_coefficient)
- [Kendall rank correlation coefficient - Wikipedia](https://en.wikipedia.org/wiki/Kendall_rank_correlation_coefficient)


## Rank biased overlap
Rank biased overlap (RBO) is a similarity metric which is more sensitive to the differences in top rankers, as opposed to correlation-based metrics which treat all entities equally. This is preferred, as in practice, the top entities are more important than the bottom entities.

- [A similarity measure for indefinite rankings | ACM Transactions on Information Systems](https://dl.acm.org/doi/abs/10.1145/1852102.1852106?casa_token=AjwNOuyOzL0AAAAA:k2VARDX1E-4U_cRY4gFMi2HVOd2W5BEqBWoHg185sIEBI1qdtN4leDZxl8eoHmnlozzOpcnh1AM)

The RBO is a concept that is fundamental to many biased similarities. Let's consider two lists of entities, $S$ and $T$, that are both sorted according to their rank. We can denote the top $d$ entities in $S$ as $S_{1:d}$. The first entry in the list, $S[0]$, is the highest ranked entity. RBO is defined as follows:
$$
\begin{align}
RBO(S,T,p):=(1-p) \sum_{d=1}^\infty p^{d-1} \frac{|S_{1:d} \cap T_{1:d}|}{d},
\end{align}
$$
The parameter $p$ (defaulting to $p=0.9$) controls the contribution of low-rank entities to RBO. The term $|S_{1:d} \cap T_{1:d}|$ represents the number of common entities for the $d$ top rankers, and dividing it by $d$ gives the fraction of common entities. This fraction is then summed over ranking, with the weight of the depth at $d$ given by $p^{d-1}$, thus giving greater weight to top rankers than to low-rank entities. 

Implementing RBO is trickly since the sum is extended over $d\rightarrow \infty$ though an implementation is available:

- [GitHub - changyaochen/rbo: Implementation of Rank-biased Overlap](https://github.com/changyaochen/rbo/tree/master)

### Truncated RBO

The original RBO takes the sum over entities beyond the ranking. Since the entities outside of the ranking is unknown, the original paper introduces an exterpolation method. But this gives many complexity with additional assumptions on the input data. So I personally prefer its truncated version, where the summation is taken for the finite ranking. Since the summation is truncated, the maximum "truncated" RBO is less than one, which makes interpretation difficult. To amend this,  I rescale the truncated RBO by dividing it by the maximum truncated sum.

$$
\begin{align}
RBO_{\text{truncated}}(S,T,p):= \dfrac{\sum_{d=1}^D p^{d-1} |S_{1:d} \cap T_{1:d}|/d}{\sum_{d=1}^D p^{d-1}}
\end{align}
$$
My implementation is available here:


- Mean Squared Error
- Normalized Discounted Cumulative Gain
- Spearman Rank-Order Correlation
- Kendall Tau Correlation
- Average Precision at K
- Normalized Mutual Information
- Jaccard Similarity
- Chu-Liu/Edmonds Algorithm

- List of metrics for rankings 
	- [Metrics for evaluating ranking algorithms - Cross Validated](https://stats.stackexchange.com/questions/159657/metrics-for-evaluating-ranking-algorithms)
- The mathematical link between MAP and DCG [Metrics for evaluating ranking algorithms - Cross Validated](https://stats.stackexchange.com/questions/159657/metrics-for-evaluating-ranking-algorithms)
