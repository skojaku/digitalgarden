---
{"dg-publish":true,"permalink":"/misc/tips/computer-and-programming/get-started-with-a-new-project/","dgHomeLink":true,"dgPassFrontmatter":false}
---


# Get started with a new project
updated: 2022-09-16


# Set up 
1. [Clone "project template" repo and follow the instruction](https://github.com/skojaku/project-template)
2. Create a shared folder in DropBox or Google Drive
3. Set up the home directory in a computer 
4. Set up the rclone (See [[Misc/tips/Computer and Programming/Automate file sharing through cloud|Automate file sharing through cloud]])

# Setting up virtual environment 

```bash
conda create -n project_env_name python=3.9
conda activate project_env_name
conda install -c conda-forge mamba -y
mamba install pytorch torchvision torchaudio cudatoolkit=11.6 -c pytorch -c conda-forge -y
mamba install -y -c bioconda -c conda-forge snakemake -y
mamba install -c conda-forge graph-tool scikit-learn numpy numba scipy pandas networkx seaborn matplotlib gensim ipykernel tqdm
```