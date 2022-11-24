---
{"dg-publish":true,"permalink":"/literature-notes/productivity/automation/faiss/","dgHomeLink":true,"dgPassFrontmatter":false}
---


# Faiss
updated: 2022-10-13


Faiss is a library for finding nearest neighbors in a high dimensional space. It is powered by GPUs and unreasonably fast thanks to smart indexing and data structure. Faiss is flexible but sometimes verbose to do a simple thing. Here I leave some snippet that I used in many projects:

## Finding k-nearest neighbors of every data point with CPU and GPUs

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
