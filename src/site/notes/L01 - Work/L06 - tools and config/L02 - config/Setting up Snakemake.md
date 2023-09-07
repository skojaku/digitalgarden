---
{"dg-publish":true,"permalink":"/l01-work/l06-tools-and-config/l02-config/setting-up-snakemake/","dgPassFrontmatter":true}
---


# Setting up Snakemake
updated: 2022-11-29
#tools/snakemake 

Snakemake is a language that defines workflow. Once you set up a workflow with Snakemake, you can run the whole pipeline from raw data all the way down to figures in your paper by pressing a button. Snakamake is fast and powerful, as it automatically parallelizes the workflow and distributes computation. 

In Snakemake, a workflow consists of *rules*. Each rule takes a file and generates another file. A rule can take another rule as input, which creates a link between rules. Snakamake creates a directed network of rules from the first input to the final output, called a *computation graph*. Then, Snakemake finds an optimal schedule to execute each rule. Snakemake does not execute a rule if its output already exists. This is super useful because we often change some parts of the workflow and want to redo only the calculations that are affected by the change.

If you are interested in the concept behind snakemake, check out [the paper](https://f1000research.com/articles/10-33/v2)

## How to set up
See [How to set up](https://snakemake.readthedocs.io/en/stable/tutorial/setup.html). An easy way to install is to use conda:
```bash
conda install -c conda-forge -c bioconda snakemake
```

## How to use it?
See the [Tutorial](https://snakemake.readthedocs.io/en/stable/tutorial/setup.html) and [my note in Japanese](https://skojaku.github.io/%E3%83%8E%E3%83%BC%E3%83%88/snakemake%E3%81%AE%E3%81%99%E3%82%9D%E3%82%81/).