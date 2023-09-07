---
{"dg-publish":true,"permalink":"/l01-work/l02-productivity-and-tools/directive-powerful-integration-of-python-scripts-into-workflow-snakemake/","dgPassFrontmatter":true}
---


# Directive - Powerful integration of python scripts into workflow - Snakemake
updated: 2022-11-29

[Snakefiles and Rules — Snakemake 7.14.2 documentation](https://snakemake.readthedocs.io/en/stable/snakefiles/rules.html#external-scripts)

`shell` and `script` are the directives that define the script to generate output files from input files. `shell` specifies the shell command, e.g., things you type in your command line. `script` specifies a script such as a python script. For instance, the following two rules produce the same output: 

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

The difference is how the variables are passed to the script. With `shell`, all variables should be given as command-line arguments. With the `script` the variables are accessible from the script. For instance, with Python, all variables are accessible via `snakemake.<directive name>` object, e.g., 
```python 
input_file = snakemake.input["input_file"]
output_file = snakemake.output["output_file"]
```

I favor `script` because it makes workflow more readable and makes it easier to pass many variables. The `shell` can be lengthy, especially when there are many variables (`input`, `output`, `params`, `resources`, etc.). With`shell`, the arguments are order sensitive, incurring an additional maintenance cost. With `script`, each parameter is specified by parameter names, which is a big plus in terms of readability. 

A drawback of the `script` is that it makes the script non-standalone; you can run it only via snakemake because otherwise, the `snakemake` object is not created. This is not a good feature when testing the hand.  One way to make it standalone is to check if `snakemake` is defined before accessing it: 
```python
import sys

If "snakemake" in sys. modules:
    vector_data_file = snakemake.input["vector_data_file"]
    clustering_model_file = snakemake.input["clustering_model_file"]
    output_file = snakemake.output["output_file"]
else:
    vector_data_file = ""
    citation_embedding_model_file = "models/clustering_model"
    output_file = "models/clustering_model"
```
This way, I can retrieve the variables from `snakemake` only when `snakemake` is created. Otherwise, I set the variables *directly* in the script so that I could run the script without `snakemake` for testing.