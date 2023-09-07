---
{"dg-publish":true,"permalink":"/l01-work/l01-research-note/ai-fairness/fairness-metrics/","dgPassFrontmatter":true}
---


# Fairness metrics
updated: 2022-12-20


## Statistical parity 

Statistical parity is a measure of fairness in a classification system, specifically in regards to the distribution of the predicted class labels for different groups in the population. It ensures that the classifier does not have a biased or disproportionate impact on certain groups, and that the predicted class labels are equally likely for all groups. To measure statistical parity, one can compare the distribution of the predicted class labels for different groups in the population. If the classifier has statistical parity, the percentage of individuals in each group who are predicted to be in a certain class should be similar. If the classifier does not have statistical parity, then the distribution of predicted class labels may be skewed or disproportionate for certain groups, indicating that the classifier is biased against those groups.

In the context of link predictions, the classifier is a link predictor that flags up node pairs if they are predicted to have an edge and otherwise flags them down. The "population" correspond to the number of node pairs between two groups. 

# References
- [Fairness through awareness | Proceedings of the 3rd Innovations in Theoretical Computer Science Conference](https://dl.acm.org/doi/10.1145/2090236.2090255)
- [Fairness in Criminal Justice Risk Assessments: The State of the Art - Richard Berk, Hoda Heidari, Shahin Jabbari, Michael Kearns, Aaron Roth, 2021](https://journals.sagepub.com/doi/full/10.1177/0049124118782533)
