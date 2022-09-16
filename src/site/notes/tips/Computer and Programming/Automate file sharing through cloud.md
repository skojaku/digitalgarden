---
{"dg-publish":true,"permalink":"/tips/computer-and-programming/automate-file-sharing-through-cloud/","dgHomeLink":true,"dgPassFrontmatter":false}
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


