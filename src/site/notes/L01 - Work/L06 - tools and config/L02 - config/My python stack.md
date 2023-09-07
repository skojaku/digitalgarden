---
{"dg-publish":true,"permalink":"/l01-work/l06-tools-and-config/l02-config/my-python-stack/","dgPassFrontmatter":true}
---



```bash
conda create -n project_env_name python=3.9
conda activate project_env_name
conda install -c conda-forge mamba -y
mamba install pytorch torchvision torchaudio cudatoolkit=11.8 -c pytorch -c nvidia -y
mamba install -y -c bioconda -c conda-forge snakemake -y
mamba install -c conda-forge graph-tool scikit-learn numpy numba scipy pandas polars networkx seaborn matplotlib gensim ipykernel tqdm black faiss-gpu==1.7.3 -y
```