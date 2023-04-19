---
{"dg-publish":true,"permalink":"/misc/productivity/automation/automate-switching-conda-environment/","dgPassFrontmatter":true}
---


# Automate switching conda environment
updated: 2022-09-16

If you work on multiple projects and have different virtual environment for each, you may spent some non-negligible amount of time for just *switching* conda environment. Here is a tip to automate this process. 

## How does it work?
Suppose that you have a directory for each project. In each directory, you have an `environment.yml` file that specifies the name of the virtual environment. When you move into a directory, a script will check the `environment.yml` file and switch the environment for you. 

## Set up
Put the following file into ~./script/ and then add
```bash
source <home>/.script/conda_auto_env.py
```

bash shell:
```bash
#!/bin/bash
#
# auto-env automatically activates a conda environment when
# entering a folder with an environment.yml file.
#
# If the environment doesn't exist, conda-auto-env creates it and
# activates it for you.
#
# To install add this line to your .bashrc or .bash-profile:
#
#       source /path/to/conda_auto_env.sh
#


function conda_auto_env() {
  if [ -e "environment.yml" ]; then
    # echo "environment.yml file found"
    ENV=$(head -n 1 environment.yml | cut -f2 -d ' ')
    # Check if you are already in the environment
    if [[ $PATH != *$ENV* ]]; then
      # Check if the environment exists
      conda activate $ENV
      if [ $? -eq 0 ]; then
      :
      else
        # Create the environment and activate
        echo "Conda env '$ENV' doesn't exist."
        conda env create -q
        source activate $ENV
      fi
    fi
  fi
}

export PROMPT_COMMAND=conda_auto_env
```

zsh:
```zsh
#!/bin/zsh

# conda-auto-env automatically activates a conda environment when
# entering a folder with an environment.yml file.
#
# If the environment doesn't exist, conda-auto-env creates it and
# activates it for you.
#
# To install add this line to your .bashrc or .bash-profile:
#
#       source /path/to/conda_auto_env.sh
#

function conda_auto_env() {
  if [ -e "environment.yml" ]; then
    # echo "environment.yml file found"
    ENV=$(head -n 1 environment.yml | cut -f2 -d ' ')
    # Check if you are already in the environment
    if [[ $PATH != *$ENV* ]]; then
      # Check if the environment exists
      conda activate $ENV
      if [ $? -eq 0 ]; then
        :
      else
        # Create the environment and activate
        echo "Conda env '$ENV' doesn't exist."
        conda env create -q
        source activate $ENV
      fi
    fi
  fi
}

precmd() { eval conda_auto_env }
```


## Reference
https://github.com/chdoig/conda-auto-env/blob/master/conda_auto_env.sh