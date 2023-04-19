---
{"dg-publish":true,"permalink":"/misc/productivity/automation/faiss/","dgPassFrontmatter":true}
---


# Faiss
updated: 2022-10-13


Faiss is a library for finding the nearest t neighbors in a high-dimensional space powered by GPUs and unreasonably fast, thanks to intelligent indexing and data structure. Faiss is flexible but sometimes verbose to do a simple thing. 

Configuring faiss is surprisingly tricky, especially when using smart approximation and GPUs. So, I wrote a helper function that makes the configuration easier:

- [Create faiss index · GitHub](https://gist.github.com/skojaku/292e433a176f594fa428cc386d758d16)


