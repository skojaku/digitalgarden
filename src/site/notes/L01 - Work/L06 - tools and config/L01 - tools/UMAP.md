---
{"dg-publish":true,"permalink":"/l01-work/l06-tools-and-config/l01-tools/umap/","dgPassFrontmatter":true}
---


# UMAP
updated: 2022-10-12
#tools/umap

[UMAP]() is a great tool to visualize a high dimensional data. It reduces the dimension by preserving local proximity of data points. 

# Faster UMAPing

The bottleneck of UMAP is the construction of the k-nearest neighbor graph. Luckly, UMAP can accept pre-computed k-nearest neighbor graph, and we have a faster library for the k-nearest neighbor graph, [faiss](). 

First of all, let's find the k-nearest neighbors using faiss.

```python
import faiss

def find_knn(emb, num_neighbors, metric="cosine", device=None):
    if metric == "cosine":
        index = faiss.IndexFlatIP(emb.shape[1])
    else:
        index = faiss.IndexFlatL2(emb.shape[1])
    if device is None:
        index.add(emb.astype(np.float32))
        distances, indices = index.search(emb.astype(np.float32), k=num_neighbors)
    else:
        try:
            gpu_id = int(device[-1])
            res = faiss.StandardGpuResources()
            index = faiss.index_cpu_to_gpu(res, gpu_id, index)
            index.add(emb.astype(np.float32))
            distances, indices = index.search(
                emb.astype(np.float32), k=num_neighbors
            )
        except RuntimeError:
            if metric == "cosine":
                index = faiss.IndexFlatIP(emb.shape[1])
            else:
                index = faiss.IndexFlatL2(emb.shape[1])
            index.add(emb.astype(np.float32))
            distances, indices = index.search(
                emb.astype(np.float32), k=num_neighbors
            )
    return indices, distances

indices, distances = find_knn(emb, num_neighbors = 5, metric = "cosine", device="cuda:0") # if you don't have gpu, set device='cpu'
```

Then, pass the identified nearest neighbors to UMAP

```python 
import umap
from pynndescent import NNDescent

index = NNDescent(emb[0, :].reshape((-1,1))) # We don't need the index but have to give something. So make up an index here. 
knn = (indices, distances, index) #data about the knn graph

# UMAPing
xy = umap.UMAP(n_neighbors=10, min_dist=0.1,precomputed_knn=knn).fit_transform(emb)
```
