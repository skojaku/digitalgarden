---
{"dg-publish":true,"permalink":"/l01-work/l06-tools-and-config/l02-config/my-python-stack/","dgPassFrontmatter":true}
---


# Install Minifoge 
- [GitHub - conda-forge/miniforge: A conda-forge distribution.](https://github.com/conda-forge/miniforge)

Miniforge is preferred over conda because Miniforge comes with mamba and conda-forge is the default channel.
# Run the following 

```bash
mamba create -n <project_name> -c rapidsai -c conda-forge -c nvidia  rapids=23.10 python=3.9 cuda-version=11.8
mamba activate <project_name>
mamba install pytorch torchvision torchaudio cudatoolkit=11.8 -c pytorch -c nvidia -y
mamba install -y -c bioconda -c conda-forge snakemake -y
mamba install -c conda-forge graph-tool scikit-learn numpy numba scipy pandas polars networkx seaborn matplotlib gensim ipykernel tqdm black faiss-gpu==1.7.3 -y
install GPUtil nvitop
```