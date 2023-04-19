---
{"dg-publish":true,"permalink":"/misc/productivity/automation/paramspace-enabling-grid-search-at-scale-snakemake/","dgPassFrontmatter":true}
---


# Paramspace - Enabling grid search at scale - Snakemake
updated: 2022-11-29
#tools/snakemake 

Snakemake provides a rich set of functions to handle parameter spaces. Yet, it gets tedious when exploring many combinations of many types of parameters. Snakemake provides a helper called `Paramspace` to handle this situation. 

- [Snakefiles and Rules — Snakemake 7.18.2.1 documentation](https://snakemake.readthedocs.io/en/stable/snakefiles/rules.html#parameter-space-exploration)

`Paramspace` takes pandas DataFrame, where each row represents a combination of parameter values. Then, `Paramspace` generates a placeholder for parameters that can be used as a part of a file name. For instance, 

```python
# declare a data frame to be a paramspace
paramspace = Paramspace(pd.read_csv("params.tsv", sep="\t"))
input_file = f"results/simulations/{paramspace.wildcard_pattern}.tsv"
```
Here, the `input_file` looks like this:
```python
"results/simulations/alpha~{alpha}_beta~{beta}_gamma~{gamma}.tsv"
```
where the alpha to gamma is parameter names taken from the columns of the input DataFrame. 

It is convenient, though I don't like creating the DataFrame. So I wrote a simple utility function that makes parameter handling easier.

[Utilities for Snakemake · GitHub](https://gist.github.com/skojaku/6284abed6406b17a86ddbfdb400df4db)

Download the `util.smk` and put it under the same folder as Snakemake resides. Then, import it by
```python
include: "./utils.smk"
```

The way it works is as follows. Suppose that I have five parameters and want to run a workflow for *every* combination of the parameters. I specify the name and value of parameters by dict as follows:
```python 
params_spherical_model = {
    "geometry":[True],
    "symmetric":[False, True],
    "aging":[False, True],
    "fitness":[True, False],
    "dim": [16, 64, 128],
}
```
Create a `Paramspace` helper by passing the dict to my utility function `to_params`:
```python
spherical_model_paramspace = to_paramspace(params_spherical_model)
```
Then, define the filename using `wildcard_pattern`, e.g., 
```python
GEOMETRIC_MODEL_FILE = f"model_{spherical_model_paramspace.wildcard_pattern}.pt"
```
You can use it as an input/output of rules, e.g., 
```python
rule model_fitting_spherical_model:
    input:
        paper_table_file = PAPER_TABLE,
        net_file = CITATION_NET,
    output:
        output_file = GEOMETRIC_MODEL_FILE
    params:
        dim = lambda wildcards : wildcards.dim,
        geometry = lambda wildcards : wildcards.geometry,
        aging = lambda wildcards : wildcards.aging,
        symmetric = lambda wildcards : wildcards.symmetric,
        fitness = lambda wildcards : wildcards.fitness,
        #in_out_coupling_strength = lambda wildcards : float(wildcards.couplingStrength)
    script:
        "workflow/fit-spherical-model/fitting.py"
```
Here, the parameter values are retrieved via `wildcards`, e.g., 
```python
dim = lambda wildcards : wildcards.dim
```
which can be accessed from the script via the `snakemake` object, e.g., 
```python
dim = snakemake.params["dim"]
```

See [[Misc/Productivity/Automation/Directive - Powerful integration of python scripts into workflow - Snakemake\|Directive - Powerful integration of python scripts into workflow - Snakemake]].