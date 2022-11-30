---
{"dg-publish":true,"permalink":"/research-note/community-detection/detectability-limit-of-communities/","dgPassFrontmatter":true}
---


# Detectability limit of communities

The detectability limit suggests that there is an information-theoretic limit in the capacity of algorithms for identifying communities in networks. Beyond this limit, no algorithm can identify the communities. 

More specifically, suppose a toy network consisting of some communities. Each community is connected within but disconnected to other communities at the begining, and we gradually break the communities by radomly rewiring the edges. Community detection algorithms can easily identify the communities if we rewire a few edges. However, as we rewire more edges, algorithms are not able to identify the communities at some points. The detectability limit is the minimum level of mixing (i.e., rewiring) above which no algorithm identifies the communities. 

The detectability limit depends on the sparsity of networks. There are two regimes of network sparsity depending on how the node degree increases with respect to the number of nodes in networks. A network is said to be dense if the average degree increases. If the average degree is constant or decreases, the networks are said to be sparse. 

**dense regime**: Degree increases with respect to the number of nodes
- Larger window size is better [[Papers/literature note/@zhangConsistencyRandomwalkBased2021\|@zhangConsistencyRandomwalkBased2021]] [[Papers/literature note/@barotCommunityDetectionUsing2021\|@barotCommunityDetectionUsing2021]]
- Non-backtracking walks improve the detectability limit of graph embedding [[Papers/literature note/@barotCommunityDetectionUsing2021\|@barotCommunityDetectionUsing2021]]
- Detectability limit for communities of different sizes [[Papers/literature note/@chenUniversalPhaseTransition2015\|@chenUniversalPhaseTransition2015]]
- Detectability limit of networks with communities of different sizes and internal strucure [[Papers/literature note/@chenPhaseTransitionsSpectral2014\|@chenPhaseTransitionsSpectral2014]]

**sparse regime**: Degree is fixed constant. 
- [[Papers/archive/Nadakuditi PRL 2012\|Nadakuditi PRL 2012]]


The detectability limit also depends on the heterogeneity in degree and community sizes. To my surprise, heterogeneity makes it easy for algorithms to identify communities.

- Ill-defined communities are more detectable than well-defined communites [[Papers/literature note/@radicchiParadoxCommunityDetection2013\|@radicchiParadoxCommunityDetection2013]]
- Degree heterogeneity accerates the ability to detect communities (for the modularity maximization) [[Papers/literature note/@radicchiDetectabilityCommunitiesHeterogeneous2013\|@radicchiDetectabilityCommunitiesHeterogeneous2013]]
- (*dense networks*) Detectability limit of networks with communities of different sizes and internal strucure [[Papers/literature note/@chenPhaseTransitionsSpectral2014\|@chenPhaseTransitionsSpectral2014]]
-  (*dense networks*) Detectability limit for communities of different sizes [[Papers/literature note/@chenUniversalPhaseTransition2015\|@chenUniversalPhaseTransition2015]]

Most study focus on the detectability limit of spectral embedding. What about nueral embedding?

-  The detectability limit of the GNN is imposed by the architecture, and the accuracy of performance in detectable regime is attributed to backpropagation [[Papers/literature note/@kawamotoMeanfieldTheoryGraph2018\|@kawamotoMeanfieldTheoryGraph2018]].  