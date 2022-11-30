---
{"dg-publish":true,"permalink":"/literature-notes/productivity/automation/wildcard-abstracting-out-file-names-snakemake/"}
---


# Wildcard - Abstracting out file names - Snakemake
updated: 2022-11-29

#tools/snakemake 


Snakemake provides a `wildcards` variable that abstracts out file names so that we can use the same abstracted file name to generate different files. This allows us to populate independent workflow in a convenient and concise way and execute them in parallel.

Suppose that you want to run a simulation $L=10$ times with different random seeds. You have $L=10$ CSV files to save the simulation results. With wildcards, this can be defined in one line code: 
```python
SIM_RESULT = "results/run_id~{run_id}.csv"
```
Here `{run_id}` is the wildcard and does not need to be specified in priori. Once the simulations are finished, you may want to plot the results in some figures and save them into pdfs. You can specify the pdf filenames using wildcards:
```python
FIG_SIM_RESULT = "figs/run_id~{run_id}.pdf"
```
The wildcard `{run_id}` creates an implicit link between `SIM_RESULT` and `FIG_SIM_RESULT` through a rule:
```python 
Rule plot:
	input:
		SIM_RESULT
	output:
		FIG_SIM_RESULT
	script:
		"plot.py"
```
Snakemake will determine that `FIG_SIM_RESULT` depends on `SIM_RESULT` with the same wildcards (e.g., `run_id`) and create a dependency graph of files. Finally, we specify  `rule_ids`.

```python
rule all:
	input:
		expand(FIG_SIM_RESULT, rule_id = list(range(5)))
```
This `all` rule specifies the final products and figures, with `run_id` integers from 0 to 4. A beauty is that snakemake will figure out all intermediate files by backtracking from the final products, creating a dependency graph, and running a series of jobs. Snakemake will run rules in parallel if their input files are independent. 