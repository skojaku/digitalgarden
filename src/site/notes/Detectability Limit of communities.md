---
{"dg-publish":true,"permalink":"/detectability-limit-of-communities/","dgHomeLink":true,"dgPassFrontmatter":false}
---


# Detectability limit of communities

The detectability limit suggests that there is an information-theoretic limit in the capacity of algorithms for identifying communities in networks. Beyond this limit, no algorithm can identify the communities. 

More specifically, suppose a toy network consisting of some communities. Each community is disconnected at the begining, and we gradually break the communities by radomly rewiring the edges. Community detection algorithms can easily identify the communities at first, but, as we rewrite more edges, they eventually fall short. The detectability limit is the minimum level of mixing (i.e., rewiring) above which no algorithm identifies the communities. This limit

**dense regime**: Degree increases with respect to the number of nodes
- Larger window size is better [[papers/literature note/@zhangConsistencyRandomwalkBased2021|@zhangConsistencyRandomwalkBased2021]] [[papers/literature note/@barotCommunityDetectionUsing2021|@barotCommunityDetectionUsing2021]]
- Non-backtracking walks improve the detectability limit of graph embedding [[papers/literature note/@barotCommunityDetectionUsing2021|@barotCommunityDetectionUsing2021]]
- Detectability limit for communities of different sizes [[papers/literature note/@chenUniversalPhaseTransition2015|@chenUniversalPhaseTransition2015]]
- Detectability limit of networks with communities of different sizes and internal strucure [[papers/literature note/@chenPhaseTransitionsSpectral2014|@chenPhaseTransitionsSpectral2014]]

**sparse regime**: Degree is fixed constant. 
- [[papers/archive/Nadakuditi PRL 2012|Nadakuditi PRL 2012]]


The detectability limit also depends on the heterogeneity in degree and community sizes. To my surprise, heterogeneity makes it easy for algorithms to identify communities.

- Ill-defined communities are more detectable than well-defined communites [[papers/literature note/@radicchiParadoxCommunityDetection2013|@radicchiParadoxCommunityDetection2013]]
- Degree heterogeneity accerates the ability to detect communities (for the modularity maximization) [[papers/literature note/@radicchiDetectabilityCommunitiesHeterogeneous2013|@radicchiDetectabilityCommunitiesHeterogeneous2013]]
- (*dense networks*) Detectability limit of networks with communities of different sizes and internal strucure [[papers/literature note/@chenPhaseTransitionsSpectral2014|@chenPhaseTransitionsSpectral2014]]
-  (*dense networks*) Detectability limit for communities of different sizes [[papers/literature note/@chenUniversalPhaseTransition2015|@chenUniversalPhaseTransition2015]]

Most study focus on the detectability limit of spectral embedding. What about nueral embedding?

-  The detectability limit of the GNN is imposed by the architecture, and the accuracy of performance in detectable regime is attributed to backpropagation [[papers/literature note/@kawamotoMeanfieldTheoryGraph2018|@kawamotoMeanfieldTheoryGraph2018]].  