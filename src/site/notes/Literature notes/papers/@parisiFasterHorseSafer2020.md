---
{"dg-publish":true,"permalink":"/literature-notes/papers/parisi-faster-horse-safer2020/","dgPassFrontmatter":true}
---


**A faster horse on a safer trail: generalized inference for the efficient reconstruction of weighted networks**
by Federica Parisi, Tiziano Squartini, Diego Garlaschelli
*IOP Publishing* (2020)
[Web](https://dx.doi.org/10.1088/1367-2630/ab74a7) [Open in zotero]( zotero://select/items/@parisiFasterHorseSafer2020)

**Tags**: 
#literature-note

---

## Summary 
This paper focuses on the class of configuration models for weighted networks and provide efficient yet maximally random weighted random networks preserving the degree and strength of nodes.

## Results
### Prevailing approaches and limitations
#### MaxENT (Chung-Lu model)
The configuration model is a random network preserving the degree of each node. The model is extended to weighted networks by considering edge weight as the number of edges and randomly placing edges with the *Chung-Lu model*. This type of configuration model is referred to as *MaxEnt* in this paper. 

While MaxEnt is probably the most used null model for weighted networks, it suffers severe limitations:
1. MaxEnt does not provide any probability model underlying edge weight, preventing us from assessment of statistical significance. 
2. MaxEnt also tends to produce dense networks if the node strength is large. 

#### IPF algorithm
For the second problem, iterative proportional fitting (IPF) algorithm has been developed, which assigns edge weights for a given network topology:

[Estimating Nonnegative Matrices from Marginal Data on JSTOR](https://www.jstor.org/stable/2525582?casa_token=gG8uBLlqjk0AAAAA%3AfaFu4yahvjZTM1PIdevSzLYQutP7neJNS6TBmNbtId4G4KEkokiXl4Bqlhngm2WMsq-whqunxYMJv8wfG6ZD4kIM-BBDzfvt2c73J4f4bhwpMCvFdg)

The IPF algorithm finds a random network closest to the given network while preserving the in and out strengths by solving a convex optimization problem with 2N constraints. Yet the IPF algorithm is deterministic, and thus the first problem remains. 

#### Density-corrected gravity model
Density-corrected gravity model (a.k.a degree-corrected gravity model) generates a random network using a directed configuration model and assigns weight to the realized edges. It assumes that the degree and strengths are well-correlated, which makes it possible to derive

[Systemic Risk Analysis on Reconstructed Economic and Financial Networks | Scientific Reports](https://www.nature.com/articles/srep15758)
While the density-corrected gravity model introduces the probability distribution over network topology, it still assigns a deterministic edge weight. 

### From maximum entropy to conditional maximum entropy
The enhanced configuration model rests upon the idea that random networks are a set of ensembles maximizing the entropy while preserving a given set of constraints (strength and degree). It leads to multiple variants, depending on whether edges are directed and/or weighted. 

This paper concerns an additional constraint, i.e., the probability $P(A)$ over network topology $A$ is given. The task is to distribute edges weights by maximizing the entropy while preserving the strength. 

*CREM-A* (CREMA for short) is an exact method, which is accurate but does not scale well for large networks. Alternatively, the authors provide a more scalable model, *CREM-B*, at expense of the exactness. CREM-B simplifies the estimation step by assuming that MaxEnt recovers the edge weights well, which is supperted empirically with two weighted networks. 



