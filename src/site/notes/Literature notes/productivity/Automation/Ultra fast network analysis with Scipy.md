---
{"dg-publish":true,"permalink":"/literature-notes/productivity/automation/ultra-fast-network-analysis-with-scipy/"}
---


# Ultra fast network analysis with Scipy
updated: 2022-11-07

Of course! 

I think your approach is simple, transparent and accessible to many people, and thus is a good way in terms of sharing. But it may not be ideal format in terms of computation cost. 

My preference is scipy csr_sparse format. It is convenient, fast, and accessible if you have scipy installed. It has a nice data structure that allows fast computation for networks. Scipy provides many useful functions for network analysis, i.e., dijkstra algorithms, finding connected components etc, too. 

The way to make it is very simple: 
net = sparse.csr_matirix((weights, (source, target)), shape=(n_nodes, n_nodes))
where source and target are the node ids, and weights are the edge weight connecting the two nodes. 

To save
```python
sparse.save_npz(net, "filename.npz")
```

And to load
```python
sparse.load_npz("filename.npz")
```


(Advanced) CSR format has a nice data structure for fast computation.  For instance, you can get neighbors of node i by 
```python
neighbors = net.indices[net.indptr[i]:net.indptr[i+1]]
```
And edge weights by 
```python
weights = net.data[net.indptr[i]:net.indptr[i+1]]
```
