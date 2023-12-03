---
{"dg-publish":true,"permalink":"/l07-inbox/tmp/cuda-setup/","dgPassFrontmatter":true}
---



# Cuda setup
updated: 2023-12-03

Check the version of cuda by 
```bash 
nvcc --version
```

If `nvcc` is not found, but you are sure that the cuda driver is installed, you have to specify the pass to the cuda driver on your .bashrc or (.zshrc if your shell is sh) as follows. Change the `cuda-12.2` appropriately. 
```bash
export PATH="/usr/local/cuda-12.2/bin:$PATH"
export LD_LIBRARY_PATH="/usr/local/cuda-12.2/lib64:$LD_LIBRARY_PATH"
```
