---
{"dg-publish":true,"permalink":"/l01-work/l06-tools-and-configuration/l02-config/ssh-setup/","dgPassFrontmatter":true}
---


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

See also: