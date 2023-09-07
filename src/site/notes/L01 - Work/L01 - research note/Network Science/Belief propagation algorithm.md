---
{"dg-publish":true,"permalink":"/l01-work/l01-research-note/network-science/belief-propagation-algorithm/","dgPassFrontmatter":true}
---


# Belief propagation algorithm
updated: 2022-11-28
#network-science/community-detection

The belief propagation algorithm is an optimal community detection method for sparse networks. 


# Papers
- Original paper: [Phys. Rev. E 84, 066106 (2011) - Asymptotic analysis of the stochastic block model for modular networks and its algorithmic applications](https://journals.aps.org/pre/abstract/10.1103/PhysRevE.84.066106) 
- [Phys. Rev. E 84, 066106 (2011) - Asymptotic analysis of the stochastic block model for modular networks and its algorithmic applications](https://journals.aps.org/pre/abstract/10.1103/PhysRevE.84.066106)
- [Scalable detection of statistically significant communities and hierarchies, using message passing for modularity | PNAS](https://www.pnas.org/doi/10.1073/pnas.1409770111)

# Code
- Python wrapper: [GitHub - skojaku/BeliefPropagation: Belief propagation method for community detection](https://github.com/skojaku/BeliefPropagation)
- Original code: [Pan Zhang's website](http://home.itp.ac.cn/~panzhang/) (You might be rejected sometimes. So try several times).

# Note
The belief propagation method does not consistently produce a good result, in large part, because of the high sensitivity to the initial condition. In fact, without a good guess about the group size and connectivity of groups, the belief propagation can easily fall short even if the communities are easily detectable. Having consulted with one of the inventors, we learn two remedies:

1. Provide a good initial `pa` and `cab` for the communities we want to detect 
2. Run the algorithm multiple times and pick the solution that achieves the lowest energy

The first remedy is helpful if we use the belief propagation algorithm as the best possible algorithm. The downside is that this remedy is not applicable to a setting where we don't have a good guess about the communities we want to detect.  The second remedy works for all settings, though it is computationally expensive. 