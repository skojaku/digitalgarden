---
{"dg-publish":true,"permalink":"/misc/tips/computer-and-programming/automating-workflow-by-snakemake/","dgHomeLink":true,"dgPassFrontmatter":false}
---


# Automating workflow by Snakemake
updated: 2022-09-30

One day at a dinner at a conference, a person next to me saying 

*"Presentation is something like---Everyone understands at the beginning. But then the audience gets confused, the chair gets confused,  and even the speaker gets confused about what he is talking about."*

Although I forgot who said this, this phrase sticks to me because I had such an experience (maybe he was talking about me). 

The same applies to experiments. At the beginning of a research project, we often start from some preliminary experiments which can be small enough to be fitted into a notebook. Everyone would understand your notebook. As the experiment gets larger in scale, your collaborators get confused, and your boss gets confused, and eventually, you get confused about what you are doing. 

Experiments are repetitive. We run dozens of dozens of experiments every day with slightly different configurations across different datasets. The design of the expermemts is often repeatedy changed during the course of project. Making the workflow in order requires huge effort and is time-comsuming. That's where Snakemake comes in.  


# Snakemake
Snakemake is a launguage to define workflow. Once you set up a workflow with Snakemake, you can run the whole pipeline from raw data, all the way down to figures in your paper by pressing a button. Snakamake is fast and powerful, as it automatically parallelizes the workflow and distributes computation. 

In Snakemake, a workflow consists of *rules*. Each rule takes a file and generates another file. A rule can take an output of another rule as input, which creates a link between rules. Snakamake creates a directed network of rules starting from the first input to the final output, which is called a *computation graph*. Then, Snakemake finds an optimal schedule to execute each rule. Snakemake does not execute a rule if it's output already exists. This is super useful because we often change some part of the workflow and want to redo only the calculations that are affected by the change.

If you are interested in the concept behind snakemake, check out [the paper](https://f1000research.com/articles/10-33/v2)

## How to set up
See [How to set up](https://snakemake.readthedocs.io/en/stable/tutorial/setup.html). An easy way to install is to use conda:
```bash
conda install -c conda-forge -c bioconda snakemake
```

## How to use it?
See the [Tutorial](https://snakemake.readthedocs.io/en/stable/tutorial/setup.html) and [my note in Japanese](https://skojaku.github.io/%E3%83%8E%E3%83%BC%E3%83%88/snakemake%E3%81%AE%E3%81%99%E3%82%9D%E3%82%81/).


# Tips 

## Use *script* directive

[Snakefiles and Rules — Snakemake 7.14.2 documentation](https://snakemake.readthedocs.io/en/stable/snakefiles/rules.html#external-scripts)

`shell` and `script` are the directives that define the process of transforming input files to output files. `shell` specifies the shell command, e.g., things you type in your command line. `script` specifies a script such as python script. For instance, the following two rules produce the same output: 

```python 
rule shell_version: 
	input: 
		input_file = UNSORTED_FILE
	output:
		output_file = SORTED_FILE
	run:
		shell("python main.py {input.input_file} {output.output_file}")

rule script_version: 
	input: 
		input_file = UNSORTED_FILE
	output:
		output_file = SORTED_FILE
	script:
		"main.py"
```

The difference is how the variables are passed to the script. With `shell`, all variables should be passed as command-line arguments. With `script`, the variables are accessible from script. For instance, with Python, all variables are accessible via `snakemake.<directive name>` object, e.g., 
```python 
input_file = snakemake.input["input_file"]
output_file = snakemake.output["output_file"]
```

I favor `script` because it makes workflow more readable and it easier to pass many variables. `shell` can be very verbose, especially when there are many variables (`input`, `output`, `params`, `resources`, etc). Furthermore, `shell` creates an implicit dependency. For instance, the arguments are order sensitive, meaning the order of arguments should be matched to that assumed in the script. This can go diseaster in many ways, e.g., misspecifying parameter values and overwriding input files.

A drawback of `script` is that it makes the script non-standalone; you can run the script only via snakemake because otherwise `snakemake` object is not created. This is not a good feature when testing the script.  One way to make it standalone is to check `snakemake` is defined, e.g., 
```python
import sys

if "snakemake" in sys.modules:
    vector_data_file = snakemake.input["vector_data_file"]
    clustering_model_file = snakemake.input["clustering_model_file"]
    output_file = snakemake.output["output_file"]
else:
    vector_data_file = ""
    citation_embedding_model_file = "models/clustering_model"
    output_file = "models/clustering_model"
```
This way, I can retrieve the variables from `snakemake` only when `snakemake` is created. Otherwise, I set the variables *directly* in the script, so that I can run the script without `snakemake`. 


## Wildcards

wildcards enabale the same rule to be applied to different files in parallel. For instance, suppose that you want to run a simulation $L=10$ times with different random seed. You have $L=10$ csv files to save the simulation results. With wildcards, this can be defined in one line code: 
```python
SIM_RESULT = "results/run_id~{run_id}.csv"
```
Here `{run_id}` is the wildcard and does not need to be specified in priori. Once the simulations are finished, you may want to plot the results in some figures and save it into pdfs. You can specified the pdf filenames using wildcards:
```python
FIG_SIM_RESULT = "figs/run_id~{run_id}.pdf"
```
The wildcard `{run_id}` creates an implicit link between `SIM_RESULT` and `FIG_SIM_RESULT` through a rule:
```python 
rule plot:
	input:
		SIM_RESULT
	output:
		FIG_SIM_RESULT
	script:
		"plot.py"
```
Snakemake will figure out that `FIG_SIM_RESULT` depends on `SIM_RESULT` with the same wildcards (e.g., `run_id`) and create a dependency graph of files. Finally, we specify  `rule_ids`

```python
rule all:
	input:
		expand(FIG_SIM_RESULT, rule_id = list(range(5)))
```
This `all` rule specifies the final products, figures, with `run_id` being integers from 0 to 4. A beauty is that snakemake will figure out all intermediate files by backtracking from the final products, creating a dependency graph, and running a series of jobs. Snakemake will run rules in parallel if their input files are independent. 


## Name files using parameter space 

## Modulize workflow
