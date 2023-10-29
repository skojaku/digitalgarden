---
{"dg-publish":true,"permalink":"/l01-work/l06-tools-and-config/l02-config/zsh-set-up/","dgPassFrontmatter":true}
---

Install the zsh script without sudo.
```bash
wget -O zsh.tar.xz https://sourceforge.net/projects/zsh/files/latest/download
mkdir zsh && unxz zsh.tar.xz && tar -xvf zsh.tar -C zsh --strip-components 1
mkdir .bin 
mv zsh .bin
cd .bin/zsh
./configure --prefix=$HOME
make
make install
```
```

Then, configure zsh as the default shell script:
```bash 

```