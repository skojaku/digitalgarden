---
{"dg-home":null,"dg-publish":true,"permalink":"/l01-work/l06-tools-and-configuration/l02-config/anaconda-setup/","dgPassFrontmatter":true}
---


## Anaconda 
Downloading and installing anaconda. And then create `.script` folder and put the following script:
```bash 
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

And add the `.script` to the execution path by adding the two lines to `.zshrc` 
```bash 
export PATH=$HOME/.script:$PATH
source $HOME/.script/conda_auto_env.sh
```

Optional
```bash
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/home/skojaku/anaconda3/lib/
```