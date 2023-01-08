---
{"dg-publish":true,"permalink":"/research-note/machine-learning/performance-metrics/","dgPassFrontmatter":true}
---


# Performance metrics
updated: 2023-01-07


## Binary vs Continuous
- [AUC-ROC](https://en.wikipedia.org/wiki/Receiver_operating_characteristic) quantifies the overlap of two distribution of metrics, one for positive $y=1$ and the other for negative $y=0$ classes. 
	- [sklearn.metrics.roc_auc_score — scikit-learn 1.2.0 documentation](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.roc_auc_score.html)
- [Average Precision](https://www.v7labs.com/blog/mean-average-precision#:~:text=Average%20Precision%20is%20calculated%20as,mAP%20varies%20in%20different%20contexts.) is useful when we are interested in a few positive examples out of a sea of data samples. One useful domain is information retrieval, where one aims to identify relevant webpages out of all web pages in the Internet.
		- [sklearn.metrics.average_precision_score — scikit-learn 1.2.0 documentation](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.average_precision_score.html#sklearn.metrics.average_precision_score)


## Multiple objectives 
- Performance profile:
	- [Performance Profiling: Theoretical Foundations, Applied Implementations and Practitioner Reflections: Journal of Sport Psychology in Action: Vol 12, No 4](https://www.tandfonline.com/doi/abs/10.1080/21520704.2020.1822970?journalCode=uspa20#:~:text=Performance%20profiling%20is%20a%20theoretically,technical%20qualities%20of%20their%20performance.)
- 