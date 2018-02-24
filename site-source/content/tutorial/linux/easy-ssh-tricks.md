---
title: "SSH Tricks"
date: 2018-02-02T12:29:49+01:00
LastModifierDisplayName: "Paál Gyula"
LastModifierEmail: "paalgyula@paalgyula.com"
draft: false
---

## SSH Tweaks/tricks

### SSH public key authentication

#### Introduction
Public-key authentication with Secure Shell is more secure than password authentication, as it provides much stronger identity checking. An entity must possess both the private key and the correct passphrase to authenticate itself to another entity.

### Generating your keypair
{{%notice warning%}}
be sure that `~/.ssh/id_rsa` doesnt exists or this command will override it!
{{%/notice%}}

```bash
ssh-keygen -t rsa -b 4096 -C "youremail@yourdomain.com"
```
This creates a new ssh key, using the provided email as a label.  
When you're prompted to "Enter a file in which to save the key," press Enter. This accepts the default file location.  
At the prompt, type a secure passphrase or leave it blank for passwordless authentication. This is not recommended by myself because if someone steal your private key, he can access your resources much easily.

