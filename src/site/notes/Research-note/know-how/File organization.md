---
{"dg-publish":true,"permalink":"/research-note/know-how/file-organization/","dgPassFrontmatter":true}
---


# File organization
updated: 2023-01-27

Almost every data science project starts by preprocessing raw data. How we organize files are critical because it may impact on the whole data analysis pipeline. 

I believe that a good file organization makes the code *mobile* and *reusable*. Mobile means that the code can run any environment (once we set up the environment appropriately with reasonable effort). Reusable means that a code written for a dataset can be used for another dataset. The mobility and reusability are critical in regard to reproduceability. 

With this philosophy in mind, I organize the files as follows.  (Disclaimer: this is a biased way optimized for network analysis with Python and Snakemake).


## Directory

At the top level, my work folder is organized into four folders, i.e., `data`, `notebooks`, `papers`, and `figs`. 

```bash
data
notebooks
papers
figs
```

All data is stored in the `data` directory, which is further divided into `raw`, `preprocessed`, and `derived`
```bash
data/raw
data/preprocessed
data/derived
```
The raw data contains all the raw data without any modification. The preprocessed folder contains the preprocessed data, where I homogenize the data types, data structure, etc, so that I can reuse the same script from a different project. 

The `preprocessed` contains the files about networks, i.e., 
```bash
preprocessed/citing2cited.npz
preprocessed/paper_table.csv
preprocessed/author2paper.npz
preprocessed/author_table.csv
preprocessed/paper2category.npz
preprocessed/category_table.csv
preprocessed/supp
```
The files with `.npz` extension are networks including a citation network (`citing2cited.npz`), an author and paper bipartite network (`author2paper.npz`), a paper and category bipartite network (`paper2category.npz`). The files with `.csv` extension stores the metadata about the data entity in the networks. The `supp` folder stores all the other data. 