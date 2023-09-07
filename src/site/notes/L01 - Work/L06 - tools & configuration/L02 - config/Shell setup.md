---
{"dg-publish":true,"permalink":"/l01-work/l06-tools-and-configuration/l02-config/shell-setup/","dgPassFrontmatter":true}
---


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