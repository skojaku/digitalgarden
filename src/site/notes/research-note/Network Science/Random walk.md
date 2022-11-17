---
{"dg-publish":true,"permalink":"/research-note/network-science/random-walk/","dgHomeLink":true,"dgPassFrontmatter":false}
---


# Random walk

updated: 2022-11-16

Random walks are instrumental to network analysis. It provides theoretical foundation of community detection, centrality analysis, routing, and embedding. 


# Random walks in a simplest form

A simplest form is random walks in undirected and unweighted networks. In this process, an agent called a walker is at a node $i$. The walker randomly chooses the next node $j$ from the neighbors of node $i$. This process is a *markov process* of the first order, i.e., the walker determines the next node based on the current node and has no memory of nodes  previously visited. 

# Variants 

### Random walks with teleportation
- [[cs/0511016] How to make the top ten: Approximating PageRank from in-degree](https://arxiv.org/abs/cs/0511016)
- [Phys. Rev. E 85, 056107 (2012) - Ranking and clustering of nodes in networks with smart teleportation](https://journals.aps.org/pre/abstract/10.1103/PhysRevE.85.056107)

### Non-backtracking walks 
- [[1501.06087] Non-backtracking spectrum of random graphs: community detection and non-regular Ramanujan graphs](https://arxiv.org/abs/1501.06087)
- [Spectral redemption in clustering sparse networks | PNAS](https://www.pnas.org/doi/10.1073/pnas.1312486110)
- [https://arxiv.org/pdf/1308.6494.pdf](https://arxiv.org/pdf/1308.6494.pdf)

### Degree-avoiding 
- [Comparison of mean hitting times for a degree-biased random walk - ScienceDirect](https://www.sciencedirect.com/science/article/pii/S0166218X14000572)
- [Phys. Rev. E 105, 044318 (2022) - Optimal exploration of random walks with local bias on networks](https://journals.aps.org/pre/abstract/10.1103/PhysRevE.105.044318) (maybe not)
- [Phys. Rev. E 89, 012803 (2014) - Characteristic times of biased random walks on complex networks](https://journals.aps.org/pre/abstract/10.1103/PhysRevE.89.012803)

### Self-avoiding walks 
- [Phys. Rev. B 27, 1635 (1983) - Asymptotic behavior of the "true" self-avoiding walk](https://journals.aps.org/prb/abstract/10.1103/PhysRevB.27.1635)
- [Phys. Rev. E 94, 042309 (2016) - Network exploration using true self-avoiding walks](https://journals.aps.org/pre/abstract/10.1103/PhysRevE.94.042309)
- [[2206.15190] Recovering network topology and dynamics via sequence characterization](https://arxiv.org/abs/2206.15190)
- [A comparative analysis of knowledge acquisition performance in complex networks - ScienceDirect](https://www.sciencedirect.com/science/article/abs/pii/S0020025520312263?via%3Dihub)
- [Knowledge acquisition: A Complex networks approach - ScienceDirect](https://www.sciencedirect.com/science/article/abs/pii/S0020025517309295?via%3Dihub)
- [[2211.06657] Identifying the perceived local properties of networks reconstructed from biased random walks](https://arxiv.org/abs/2211.06657)

### Node2Vec walks
- [node2vec | Proceedings of the 22nd ACM SIGKDD International Conference on Knowledge Discovery and Data Mining](https://dl.acm.org/doi/10.1145/2939672.2939754)
- [Analysis of node2vec random walks on networks | Proceedings of the Royal Society A: Mathematical, Physical and Engineering Sciences](https://royalsocietypublishing.org/doi/10.1098/rspa.2020.0447)

### Fairness-aware walks 
- [Fairwalk: Towards Fair Graph Embedding | IJCAI](https://www.ijcai.org/proceedings/2019/456)
- [[2105.02725] CrossWalk: Fairness-enhanced Node Representation Learning](https://arxiv.org/abs/2105.02725)


# Review 
- [Random walks and diffusion on networks - ScienceDirect](https://www.sciencedirect.com/science/article/pii/S0370157317302946?via%3Dihub)
- [A Guide to Temporal Networks: Second Edition (Complexity Science): Naoki Masuda, Renaud Lambiotte: 9781786349156: Amazon.com: Books](https://www.amazon.com/Guide-Temporal-Networks-Complexity-Science/dp/1786349159) 