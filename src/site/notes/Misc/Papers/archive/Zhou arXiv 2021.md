---
{"dg-publish":true,"permalink":"/misc/papers/archive/zhou-ar-xiv-2021/","dgPassFrontmatter":true}
---



Zhou, K., Ethayarajh, K., & Jurafsky, D. (2021). _Frequency-based Distortions in Contextualized Word Embeddings_. http://arxiv.org/abs/2104.08465

# Summary
- **Research question** How does word frequency in pre-training data affect the behavior of similarity metrics in contextualized BERT embeddings? Are there systematic ways in which some word relationships are exaggerated or understated?
- **Approach** By measuring the size of the distribution of frequent and rare words, and the similarity between them, they explore the impact of the frequency on embedding. They also compare the similarity with that judged by humans. 
- **Results** Popular words tend to have a wider distribution in the embedding. Also, the gap between similarity by embedding and by human experts isd different, and the difference is correlated with the frequency of words.
- **Implication** Data are by nature biased as it reflects an aspect of the real world. Even if the data is not biased, there would still be a distortion. It is, therefore, critical to bringing awareness to the potential inequalities that exist in the dataset as well as the models that are trained on them. Fine-tuning models to take on a variety of distortions could give rise to new perspectives and help provide a more diverse and grounded representation of the world.
