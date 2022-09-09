---
{"dg-publish":true,"permalink":"/research-note/ai-fairness/biases-in-a-is/","dgHomeLink":true,"dgPassFrontmatter":false}
---


# Biases in AIs

Artificial intelligence (AI) is a reflection of ourselves. It learns from what we said, what we did, and how we did, including unwanted bias. Driven by the advent of big data and powerful neural networks, AIs are capable of learning complex patterns from big data. The data are collected from a variety of sources, including the ones with questionable societal biases against specific populations. This is a recipe of biased AIs.

- **Example of AI bias**
	- [Gender and racial bias in DALL-E](https://www.vox.com/future-perfect/23023538/ai-dalle-2-openai-bias-gpt-3-incentives)
	- [AI’s Islamophobia problem](https://www.vox.com/future-perfect/22672414/ai-artificial-intelligence-gpt-3-bias-muslim?utm_source=Sailthru&utm_medium=email&utm_campaign=Future%20Perfect%204-12-22&utm_term=Future%20Perfect)
	- [Google Translate from Spanish into English, phrases reffering to woman often becom "he said" or "he wrote"](https://www.independent.co.uk/life-style/women/google-translate-sexist-masculine-feminine-he-said-she-said-english-spanish-languages-a8672586.html)
	- [Sorftware designed to warm people using Nikon cameras when the person are photographing seems to be blinking tends to interpret Asians as always blinking ](https://thesocietypages.org/socimages/2009/05/29/nikon-camera-says-asians-are-always-blinking/)
- **Origin of bias**
	- [More than 45% of ImageNet, a dataset used to train image DL, comes from the United States, comparsing 4% of the world's population](https://venturebeat.com/2020/11/03/researchers-show-that-computer-vision-algorithms-pretrained-on-imagenet-exhibit-multiple-distressing-biases/)
	- [Machine learning for medicine can be biased. A DL that is trained on 129,450 images to find skin cancer failed to work for black-skin people due to the skewness of the dark-skin people](https://www.theatlantic.com/health/archive/2018/08/machine-learning-dermatology-skin-color/567619/)
	- [Wikipedia, a diverse and rich crowd data sources, has bibliographies, of which 18 % of are on women](https://en.wikipedia.org/wiki/Gender_bias_on_Wikipedia)
- **Understanding the maniufold of embedding**
	- Word embedding reflects undesirable societal bias such as gender [[papers/archive/Bolukbasi NIPS 2016|Bolukbasi NIPS 2016]]. 
	-  SGNS produces a gender neutral embedding for most words but amplifies the gender-bias for gender specific words [[papers/archive/Ethayarajh ACL 2019|Ethayarajh ACL 2019]].
	- SGNS and word frequency: [[papers/archive/Zhou arXiv 2021|Zhou arXiv 2021]] [[papers/archive/Ethayarajh ACL 2019b|Ethayarajh ACL 2019b]]
	- Bias in graph embedding [[papers/archive/Edwards ICML 2016|Edwards ICML 2016]][[papers/archive/Bose ICML 2019|Bose ICML 2019]] [[papers/archive/Khajehnejad arXiv 2021|Khajehnejad arXiv 2021]]
	- Friendship paradox [[Friendship paradox|Friendship paradox]]
	- Bias in contextualized embeddings [[papers/archive/Christine ACL 2019|Christine ACL 2019]] [[papers/archive/Kurita ACL 2019|Kurita ACL 2019]]
	- Bias mining [[papers/archive/Swinger AAAI 2019|Swinger AAAI 2019]]
	- Bias is covered by debiasing method but not removed [[papers/archive/Hila Gonen  NAACL 2019|Hila Gonen  NAACL 2019]]
- **Metrics and benchmark for biases**
	- SemBias [[papers/archive/Zhao ACL 2018|Zhao ACL 2018]]
	- Direct and Indirect biases [[papers/archive/Bolukbasi NIPS 2016|Bolukbasi NIPS 2016]]
	- Percent Male neighbors (PMN) [[papers/archive/Gonen ACL 2019|Gonen ACL 2019]] 
	- WEAT statistic [[papers/archive/Aylin Caliskan Science 2017|Aylin Caliskan Science 2017]], Generalized WEAT for multi-categories [[papers/archive/Swinger AAAI 2019|Swinger AAAI 2019]]
	- [Relative Negative Sentiment Bias](https://aclanthology.org/P19-1162v2.pdf)
	- Nearest neighbor approach [[papers/archive/Hila Gonen  NAACL 2019|Hila Gonen  NAACL 2019]]
- **Debiasing**
	- Projection [[papers/archive/Bolukbasi NIPS 2016|Bolukbasi NIPS 2016]]
	- Debiasing by learning [[papers/archive/Zhao ACL 2018|Zhao ACL 2018]]
	- Identifyng biased curpos [[papers/archive/Mark-Etienne Brunet ICML 2019|Mark-Etienne Brunet ICML 2019]]
	- Iterative Null space projection [[papers/archive/Shauli Ravfogel ACL 2020|Shauli Ravfogel ACL 2020]]
	- [Open AI's effort in debiasing DALL-E](https://github.com/openai/dalle-2-preview/blob/main/system-card.md?utm_source=Sailthru&utm_medium=email&utm_campaign=Future%20Perfect%204-12-22&utm_term=Future%20Perfect)
	- [Debiasing GPT-3 by fine-tuning with curated datasets](https://proceedings.neurips.cc/paper/2021/hash/2e855f9489df0712b4bd8ea9e2848c5a-Abstract.html)
- **Issues in analogy test to quantify bias**
	- Critical problem of analogy tests on embeddings [[papers/archive/Nissim ACL 2020|Nissim ACL 2020]]
	- The answer x to the analogy "a:b :: b:x?" often is close to b. [[papers/archive/Anna Rogers SEM 2017|Anna Rogers SEM 2017]] [Linzen](https://aclanthology.org/W16-2503.pdf)
	- What is analogy, and why embedding approaches fail? [[papers/archive/Anna Rogers SEM 2017|Anna Rogers SEM 2017]]
	- https://aclanthology.org/S17-1017/
	- https://arxiv.org/abs/1903.03862
	- https://arxiv.org/abs/1904.04047
