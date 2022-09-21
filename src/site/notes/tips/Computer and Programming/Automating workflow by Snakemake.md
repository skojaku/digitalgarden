---
{"dg-publish":true,"permalink":"/tips/computer-and-programming/automating-workflow-by-snakemake/","dgHomeLink":true,"dgPassFrontmatter":false}
---


# Automating workflow by Snakemake
updated: 2022-09-21

One day at a dinner at a conference, a person next to me saying 

*"Presentation is something like---Everyone understands at the beginning. But then the audience gets confused, the chair gets confused,  and even the speaker gets confused about what he is talking about."*

Although I forgot who said this, this phrase sticks to me because I had such an experience (maybe he was talking about me). 

The same applies to experiments. At the beginning of a research project, we often start from some preliminary experiments which can be small enough to be fitted into a notebook. Everyone would understand your notebook. As the experiment gets larger in scale, your collaborators get confused, and your boss gets confused, and eventually, you get confused about what you are doing. 

Experiments are repetitive. We run dozens of dozens of experiments every day with slightly different configurations across different datasets. The design of the expermemts is often repeatedy changed during the course of projects. Making the workflow in order requires huge effort and time-comsuming. That's where Snakemake comes in.  


# Snakemake
Snakemake is a launguage to define workflow. Once you set up a workflow with Snakemake, you can run the whole pipeline from raw data all the way down to figures in your paper with one-press of button. Snakamake is fast and powerful, as it automatically parallelizes the workflow and distributes computation. 

In Snakemake, a workflow consists of *rules*. Each rule takes a file and generates another file. A rule can take an output of another rule as input, which creates a link between rules. Snakamake creates a directed network of rules starting from the first input to the final output, which is called a *computation graph*. Then, Snakemake finds an optimal schedule to execute each rule. Snakemake does not execute a rule if it's output already exists. This is super useful because we often change some part of the workflow and want to redo only the calculations that are affected by the change.

## How to set up
See [How to set up](https://snakemake.readthedocs.io/en/stable/tutorial/setup.html). I think the easiest way to install is to use conda:
```bash
conda install -c conda-forge -c bioconda snakemake
```

## How to use it?
See the [Tutorial](https://snakemake.readthedocs.io/en/stable/tutorial/setup.html) and [my note in Japanese](https://skojaku.github.io/%E3%83%8E%E3%83%BC%E3%83%88/snakemake%E3%81%AE%E3%81%99%E3%82%9D%E3%82%81/).


# Tips 
Snakemake is unique and actively developing. Everytime I visit the website, there are always new features. In every project, I learn new features :smile: and write a more conscise and clearn workflow :fire: Here is an imcomplete list of my curation of tips. 


