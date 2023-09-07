---
{"dg-publish":true,"permalink":"/l01-work/l02-productivity-and-tools/get-started-with-a-new-computer/","dgPassFrontmatter":true}
---


# Get started with a new computer
updated: 2022-09-16


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

## zsh without sudo 

Donwload the zsh script
```bash 
wget -O zsh.tar.xz https://sourceforge.net/projects/zsh/files/latest/download
mkdir zsh && unxz zsh.tar.xz && tar -xvf zsh.tar -C zsh --strip-components 1
cd zsh
```
and compile by make 
```bash
./configure --prefix=$HOME/.bin
make
make install
```
and add the following line to `.bashrc`
```bash
[ -f $HOME/bin/zsh ] && exec $HOME/bin/zsh -l
```

Add a path to conda by copying `conda initialize` blcok in `.bashrc` to `.zshrc`.  And install oh-my-zsh if prefer. 

## ssh 
### Set up public key authentification
(Assume MacOS)

```bash
ssh-add --apple-use-keychain  
ssh-add -l  
```  
  
The first command will load your ssh key to the MacOS native keychain. It should as you for your passphrase. If it's successful, the second command will show you the loaded key that looks like:  

```bash
Identity added: /User/your_username/.ssh/your_ssh_key  
```
  
Then create a `~/.ssh/config` file if you don't have one with the following contents:  

```
Host *  
    UseKeyChain yes  
    ForwardAgent yes  
```
  
The last two lines should be indented (with at least one space character). Frequently the ServiceNow got rid of the indentation.  
  
b) ssh into a remote. It shouldn't ask you for passphrase; i.e., you should be able to ssh into the remote without doing anything (since your ssh key was loaded into the MacOS's keychain). Once there, try  

```bash
ssh-add -l  
```
  
again. It should show you the loaded key (instead of the "Could not open a connection to your authentication agent." as shown in your screenshot.  

