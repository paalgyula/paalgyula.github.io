---
title: "Letsencrypt Acme Nginx"
LastModifierDisplayName: "Paál Gyula"
LastModifierEmail: "paalgyula@paalgyula.com"
date: 2018-01-31T19:08:01+01:00
draft: false
---

## Introduction

This is a guide how to set up your **free SSL certificate** for your web-server with [Letsencrypt](https://letsencrypt.org/)'s acme client on an *Ubuntu linux server*.

## Installation

First of all we have to install the NGINX web server

```
sudo apt install nginx
```

Next step is to install the certbot via the certbot's lauchpad repository

```
sudo apt-get install software-properties-common
sudo add-apt-repository ppa:certbot/certbot
sudo apt-get update
sudo apt-get install certbot python-certbot-nginx
```

We have all dependency installed so lets configure it!

## Configuration

First step is to configure our virtualhost in nginx for example we will use *example.com* domain

{{% notice tip %}}
The example.com is just an example you should change it to your domain name!
{{% /notice %}}

lets create a new file at /etc/nginx/sites-available/example.com 

```
sudo nano /etc/nginx/sites-available/example.com
```

paste the following code:

```
server {
	listen 80;
	listen [::]:80;

	server_name example.com;

	root /var/www/example.com;
	index index.html;

	location / {
		try_files $uri $uri/ =404;
	}
}
```
Lets create a directory for our website content:
```
sudo mkdir -p /var/www/example.com
```

Now we can enable the site by creating symlink at NGINX's sites-enabled folder, and restart the server:
```
sudo ln -s /etc/nginx/sites-available/example.com /etc/nginx/sites-enabled/example.com
sudo service nginx restart
```
We previously installed the certbot's NGINX plugin so the plugin will guide us trough the configuration cycle. Lets start the client with the following command:
```
sudo certbot
```
The certbot will find our predefined virtualhost something like this:
![Certbot Step 1](/images/screenshots/certbot_step_1.png "Certbot Step 1")
You should type `1` (or the id of your domain) and press Enter

After this there will be some question you should fill, then in the end the script will ask for what will you gonna do with the plain HTTP traffic. I suggest use the redirect method which is the **2nd option**, this option will redirect all unencrypted traffic to HTTPS channel. Select `2` and then press `Enter`.

If everything is OK you should see something like:

```
Congratulations! You have successfully enabled https://example.com
```

{{% notice warning %}}
**You're not done!** All of the certs aquired from LetsEncrypt.org **expires in 3 months**
{{% /notice %}}

### Configuring automatical renew

Theres a quick solution to renew your cert automatically. The certbot client has a great command line feature which can renew your certificate with just one command: `certbot renew`  
Now we just need a cron script what is executing every day and checks for expired cert/certs.
Create a file in `/etc/cron/cron.daily` called `certbot-renew`:
```
sudo nano /etc/cron/cron.daily/certbot-renew
```
Paste the following content:
```
#!/bin/bash
certbot renew

```

Add the executable flag on the file: 
```
sudo chmod +x /etc/cron/cron.daily/certbot-renew
```

**Congratulations, now you have finished! :)**
