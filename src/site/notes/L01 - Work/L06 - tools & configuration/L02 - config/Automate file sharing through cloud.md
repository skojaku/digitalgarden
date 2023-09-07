---
{"dg-publish":true,"permalink":"/l01-work/l06-tools-and-configuration/l02-config/automate-file-sharing-through-cloud/","dgPassFrontmatter":true}
---


# Automate file sharing
updated: 2022-09-16


## rclone 
rclone connects a server with major cloud file storage services like Google Drive and DropBox. By running it as a deamon, it will keep files under a specified folder up-to-date.

- [Youtube](https://www.youtube.com/watch?v=f8K-V3HHDA0&t=232s)
```bash
mkdir <dirname>
rclone mount --daemon <drivename>:<path> <dirname>
```


