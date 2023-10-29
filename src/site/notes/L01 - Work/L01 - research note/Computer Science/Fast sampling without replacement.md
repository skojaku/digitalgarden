---
{"dg-publish":true,"permalink":"/l01-work/l01-research-note/computer-science/fast-sampling-without-replacement/","dgPassFrontmatter":true}
---


# Sampling without replacement 
updated: {{date}}

## Efraimidis-Spirakis algorithm 

#### Reference:
[Weighted random sampling with a reservoir - ScienceDirect](https://www.sciencedirect.com/science/article/abs/pii/S002001900500298X)

#### Algorithm
- **Input**: $n$ weight $w=[w_1,\ldots,w_n]$ and the number of $m$ samples to draw
- **Output**: $m$ samples without duplicates 
- **Operation**:
	1. Draw a uniform random variable $u_i$ for each item 
	2. Compute a random variable $X_i = u_i ^{1/w_i}$
	3. Find the indices of the $m$ largest values. 
	4. Return the indices
#### Implementation tips

Since $1/w_i$ can be arbitrarily large and cause overfloating, it would be preferred to transform $X_i$ by 
$$
Z_i:=\log(X_i) =\frac{1}{w_i} \log(u_i)
$$
The logarithmic transformation preserves the order $X_i$. Thus, instead of using $X_i$, we can use $Z_i$ to find what indices to return. 

#### Code
