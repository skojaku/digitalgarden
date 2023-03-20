---
{"dg-publish":true,"permalink":"/representation-learning/","dgPassFrontmatter":true}
---


# Representation learning
updated: 2023-02-16

Representation is a description of objects, knowledge, and concepts. Creating a representation is a *dimensionality reduction problem*, as it reduces complex objects into a much simpler form (e.g., words, symbols, paintings) that can be communicated and stored.  Representation involves summarization or abstraction, in which we remove redundancy and distill the essence of objects. 

### Historical context
Representation is a fundamental aspect of human cognition and communication and plays a key role in our ability to understand the world around us. Lascaux's cave painting, for example, is probably the oldest depiction of nature, with an age estimated at around 17,000. It's hard not to be surprised that these lively animals were depicted in colors with the proper perspective already at that time. The caving is a rich and detailed *representation* of their culture and perception of the world, passed down from generation to generation.

![](https://upload.wikimedia.org/wikipedia/commons/thumb/1/1e/Lascaux_painting.jpg/440px-Lascaux_painting.jpg)

Representation has been a vital means of communicating and sharing knowledge. Digital technology has enabled us to create more complex and detailed representations than ever before, offering new opportunities for insight and discovery. At the same time, it presents new challenges in understanding and exploiting the increasing volume and complexity of representation.

![](https://miro.medium.com/max/799/1*tV_6-fK-G3wDs2DrybRgpw.jpeg)

The increasing capacity of medium representation calls for a need to summarize complex representations into a compact yet useful representation. To make a good simple representation, the conventional option is to hand design representations that are likely to be useful. However, this heavily relies on domain expertise and requires considerable burden.

### Representation learning
*Representation learning* goes beyond human cognitive limitations by making use of powerful machines. Representation learning is essentially dimensionality reduction, where high-dimensional representations are projected onto a low-dimensional representation while maintaining crucial features. From this perspective, Principal Component Analysis (PCA) and Linear Discriminant Analysis (LDA) are probably the most widespread *linear* representation learning. In 2000, Science published two exciting papers about *non-linear* dimensionality reduction methods, one about Isomap and the other about Locally Linear Embedding (LLE):
- [Nonlinear Dimensionality Reduction by Locally Linear Embedding | Science](https://www.science.org/doi/10.1126/science.290.5500.2323)
- [A Global Geometric Framework for Nonlinear Dimensionality Reduction | Science](https://www.science.org/doi/full/10.1126/science.290.5500.2319?casa_token=nc3NyNR0iz0AAAAA%3A1lImKGXkcKIvwQGBZ_wKntkK7Bl37LUGRkNLdtIoH39XfQ7h8cFPmvKjUfLzh1vRNlHvIXLkdetB)
I also like Diffusion maps, as it is grounded on a physical diffusion process characterized by random walks:
- [Geometric diffusions as a tool for harmonic analysis and structure definition of data: Diffusion maps | PNAS](https://www.pnas.org/doi/10.1073/pnas.0500334102)
See also the graph representation learning framework that unifies a diverse array of embedding methods:
- [Graph Embedding and Extensions: A General Framework for Dimensionality Reduction | IEEE Journals & Magazine | IEEE Xplore](https://ieeexplore.ieee.org/document/4016549)
These dimensionality reduction methods require us to make one critical design decision, i.e., distance metric. In other words, we have to define how to measure the similarity/distance of two entities from which the representation is generated. However, designing a good distance metric brings us back to the problem of finding good features and how we weight them. 

### Neural representation learning
Neural networks iteratevely transform input data down to the final output. At each layer, the given datum creates a unique activation pattern, and this pattern is its representation. Godfather of deep neural network, Geoffrey Hinton, put:

> **Deep-learning methods are representation-learning methods** with multiple levels of representation, obtained by composing simple but non-linear modules that each transform the representation at one level (starting with the raw input) into a representation at a higher, slightly more abstract level.

in his perspective paper in Nature [Deep learning | Nature](https://www.nature.com/articles/nature14539). The idea of neural nets as a representation learner dates back to 1986, in a paper by David Rumelhart, Geoffrey Hinton & Ronald Williams:

- [Learning representations by back-propagating errors | Nature](https://www.nature.com/articles/323533a0),

where a neural network was trained to learn a family tree and produced the following six-dimensional representation of people reflecting the name origins and generations. I was excited to know that the first neural representation learning was graph embedding!
![](https://chsasank.com/assets/images/classic_papers/backprop/fig4.png)
Neural representation learning took off, but it had been largely ignored because neural networks suffer from overfitting and gradient diffusion. But these two problems were solved in 2006 by two papers by Geoffrey Hinton:

- [Reducing the Dimensionality of Data with Neural Networks | Science](https://www.science.org/doi/10.1126/science.1127647)
- [A fast learning algorithm for deep belief nets | Neural Computation](https://dl.acm.org/doi/10.1162/neco.2006.18.7.1527)

### One-fits-many representation
Data representation had been a manual supervised human learning problem. Data representation is often tailored for a particular task of interest based on human domain knowledge, which is rarely helpful for other tasks unless the task of interest is so general enough to be relevant to other tasks. 

Unsupervised machine learning offers new opportunities to create a single representation that fits many tasks. In particular, neural representation learning has shown its effectiveness in creating a versatile, valuable representation for many tasks. 

###  Complexity vs. Interpretability
So what's unique about neural representation learning in contrast to traditional dimensionality reduction methods? The defining characteristic of neural networks is their compositional flexibility, allowing us to easily build a highly complex neural network by introducing new layers, bypass, non-linearity, convolusion, pooling, and attentional operations, which are all jointly learned from data. At the same time, this complexity makes it unclear what the learned representation actually represents. 

### Unpacking black box representation
- [Linear autoencoders do PCA | Virie's mindset](https://pvirie.wordpress.com/2016/03/29/linear-autoencoders-do-pca/)
- [From Principal Subspaces to Principal Components with Linear Autoencoders](https://arxiv.org/abs/1804.10253)


In the same year, this paper introduces the Sparsifying Logistic activation function to learn a spatial representation. I find it interesting because it promotes sparsity with the non-linear activation function instead of commonly used lasso regularization. 

- [Efficient Learning of Sparse Representations with an Energy-Based Model](https://papers.nips.cc/paper/2006/hash/87f4d79e36d68c3031ccf6c55e9bbd39-Abstract.html)

