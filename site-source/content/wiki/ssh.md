---
title: "Secure Shell (SSH)"
date: 2018-02-02T12:35:12+01:00
LastModifierDisplayName: "Paál Gyula"
LastModifierEmail: "paalgyula@paalgyula.com"
draft: false
---
### SSH - Secure Shell

SSH (Secure SHell) is an encrypted terminal program that replaces the classic telnet tool on Unix-like operating systems.

In addition to remote terminal access provided by the main ssh binary, the SSH suite of programs has grown to include other tools such as *[SCP](#scp-secure-copy)* (Secure Copy Program) and *[SFTP](#sftp-secure-file-transfer-protocol)* (Secure File Transfer Protocol).

### SFTP - Secure File Transfer Protocol
The SSH File Transfer Protocol (also Secure File Transfer Protocol, or SFTP) is a network protocol that provides file access, file transfer, and file management over any reliable data stream. It was designed by the Internet Engineering Task Force (IETF) as an extension of the Secure Shell protocol (SSH) version 2.0 to provide secure file transfer capabilities.

### SCP - Secure Copy
The SCP is a network protocol, based on the BSD RCP protocol, which supports file transfers between hosts on a network. SCP uses Secure Shell (SSH) for data transfer and uses the same mechanisms for authentication, thereby ensuring the authenticity and confidentiality of the data in transit. A client can send (upload) files to a server, optionally including their basic attributes (permissions, timestamps). Clients can also request files or directories from a server (download). SCP runs over TCP port 22 by default. Like RCP, there is no RFC that defines the specifics of the protocol.