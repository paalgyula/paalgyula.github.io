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
```bash
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

