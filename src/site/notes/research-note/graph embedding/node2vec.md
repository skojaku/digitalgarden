---
{"dg-publish":true,"permalink":"/research-note/graph-embedding/node2vec/","dgHomeLink":true,"dgPassFrontmatter":false}
---


# Node2Vec

node2vec is a direct application of word2vec optimized with negative sampling. 

# Packages
- [Implementation by the authors of the node2vec paper](https://github.com/aditya-grover/node2vec) This is one of the most cited repo of node2vec. However, this code hasn't been maintained for years and is slow. But this is a well-accepted baseline package. 
- [node2vec in pip package](https://github.com/eliorc/node2vec) This one has many stars probably because it uses `node2vec` in pypi. However, this node2vec often underperforms because of a bad hyperparameter configuration. Furthermore, this node2vec is extremely slow and memory demanding and not scalable to large networks. 
- [fastnode2vec](https://github.com/louisabraham/fastnode2vec) This is the fastest implementation of node2vec and generally runs 3-5 times with performance comparable to the original implementation of node2vec. See his [blog](https://louisabraham.github.io/articles/node2vec-sampling.html) if you are interested in the magic behind fastnode2vec. 
- [pecanpy](https://github.com/krishnanlab/PecanPy/tree/7c1d874c17bcdbdc3a56c19a38eb3f3e440f009b) This only provides command-line client. Not usable.
- [node2vec in pytorch geometric](https://pytorch-geometric.readthedocs.io/en/latest/index.html) Pytorch implementation of node2vec. Useful if you work with pytorch. 

All packages except the pytorch geometric are built on top of word2vec implemented in [gensim](https://radimrehurek.com/gensim/).

# Parameter configuration  
node2vec has several parameters to define random walks in networks together with the parameters for gensim (word2vec).
- Random walks
	- Window length defines the number of steps a walker makes in a single run. Larger length yields a better result with diminishing return. A good value is typically 80. 
	- `num_walks` specifies the number of walkers starting from each node. Larger is better at the expense of computation time and memory. A good value ranges between 10 or 20. If the network is directed, set a larger value like 30 and 40. 
	- `p` is inversely proportional to the probability of backtrack. Less likely a walker backtracks if $p$ is higher. 
	- `q` is inversely proportional to the probability of visiting a common neighbor of the previously visited node. Less likely a walker visits the common neighbor if $q$ is higher. 
- Gensim (word2vec)
	- `context` or `window_length` defines the length of context window. It controls the resolution of the structure to be preserved in the embedding, i.e., smaller window size preserves more local structure. Set `window_length = 10` if you have no preference.
	- `batch_walk` or `batch_size` is the number of data samples with which to calculate a gradient. Larger is better. Set `batch_walk = 10000` if you have no preference. 
	- `workers` is the number of CPU cores to train word2vec. 
	- `epochs`  (or `iter` in gensim version 3.9 or less) is the number of times we go through the given sentences.  Larger is better but `epochs=1` works enough in many cases. 
	- `ns_exponent` is the exponent of word frequency distribution used to generate negative samples. Set `ns_exponent = 0.75` or `1`  if no preference. 

# Properties
- node2vec generates an embedding that does not have information about degree (provided that `ns_exponent=1`) [paper](https://proceedings.neurips.cc/paper/2021/hash/ca9541826e97c4530b07dda2eba0e013-Abstract.html)
- node2vec can be imterpreted as an implicit matrix factorization and be trained using spectral methods [paper](https://dl.acm.org/doi/abs/10.1145/3159652.3159706)
- node2vec is equivalent to [[LINE|LINE]] if `context` or (`window_length`) is one. [paper](https://dl.acm.org/doi/abs/10.1145/3159652.3159706)
- We can encode different structures (e.g., community and core-periphery structure) by changing `p` and `q`. [paper](https://snap.stanford.edu/node2vec/)
- Connectedness is important. Isolated nodes can drastically change embedding. Always remove isolated nodes before feeding into it. 