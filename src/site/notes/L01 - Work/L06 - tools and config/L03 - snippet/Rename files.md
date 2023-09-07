---
{"dg-home":null,"dg-publish":true,"permalink":"/l01-work/l06-tools-and-config/l03-snippet/rename-files/","dgPassFrontmatter":true}
---


# Rename files 

To install, 

```
conda install -c bioconda rename
```

Rename 
```
rename 's/-/_/g' aps-journal-net.npz
```

To dry-run, put `-n` as the option.
```
rename -n 's/-/_/g' aps-journal-net.npz
```

bash script:
```
for f in *.npz
do
    newf=$(echo $f| sed "s/net=/net_/g")
    mv $f $newf
done
```