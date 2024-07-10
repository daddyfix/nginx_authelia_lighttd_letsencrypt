# Self Hosting Domain Authetication Tutorial on Linux

## Introduction

### 1. Overview of the Tutorial

This tutorial will help you install a self hosted Single-Sign-On solution with Nginx Proxy Manager, Lighttpd, Authelia, and Certbot for multiple domains.
Took me a while to put all these pieces together. Hopefully someone can use this small tutorial

1. [Nginx Proxy Manager (NPM)](https://nginxproxymanager.com/) comes as a pre-built docker image that enables you to easily forward to your websites running at home or otherwise, including free SSL, without having to know too much about Nginx or Letsencrypt.
    
2. [Authelia](https://www.authelia.com/) is an open-source authentication and authorization server and portal fulfilling the identity and access management (IAM) role of information security in providing multi-factor authentication and single sign-on (SSO) for your applications via a web portal. It acts as a companion for common reverse proxies.

3. [lighttpd](https://www.lighttpd.net/) (pronounced /lighty/) is a secure, fast, compliant, and very flexible web server that has been optimized for high-performance environments. lighttpd uses memory and CPU efficiently and has lower resource use than other popular web servers. Its advanced feature-set (FastCGI, CGI, Auth, Output-Compression, URL-Rewriting and much more) make lighttpd the perfect web server for all systems, small and large. lighttpd is released under the Open Source revised BSD license.

4. [cerbot](https://certbot.eff.org/) is a free, open source software tool for automatically using Let’s Encrypt certificates on manually-administrated websites to enable HTTPS.
   

### 2. Prerequisites

You have one or more Linux Servers ready to manages the services above. This is my setup...

#### Hardware and OS

+ Linux 5.15.0-113-generic x86_64 GNU/Linux
+ Ubuntu 22.04 (jammy)
  
#### OS Software

1. [Nginx Proxy Manager (NPM)](https://nginxproxymanager.com/) comes as a pre-built docker image that enables you to easily forward to your websites running at home or otherwise, including free SSL, without having to know too much about Nginx or Letsencrypt.
    
2. [Authelia](https://www.authelia.com/) is an open-source authentication and authorization server and portal fulfilling the identity and access management (IAM) role of information security in providing multi-factor authentication and single sign-on (SSO) for your applications via a web portal. It acts as a companion for common reverse proxies.

3. [lighttpd](https://www.lighttpd.net/) (pronounced /lighty/) is a secure, fast, compliant, and very flexible web server that has been optimized for high-performance environments. lighttpd uses memory and CPU efficiently and has lower resource use than other popular web servers. Its advanced feature-set (FastCGI, CGI, Auth, Output-Compression, URL-Rewriting and much more) make lighttpd the perfect web server for all systems, small and large. lighttpd is released under the Open Source revised BSD license.

4. [cerbot](https://certbot.eff.org/) is a free, open source software tool for automatically using Let’s Encrypt certificates on manually-administrated websites to enable HTTPS.

## Setting Up Nginx Proxy Manager

1. [Install docker with apt](https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository)
2. Create a path to you docker compose file
   ```bash
   mkdir -p ~/docker/nginx-proxy-manager
   cd ~/docker/nginx-proxy-manager
   touch docker-compose.yml
   ```
3. Edit docker-compose.yml
   ```bash
   services:
    app:
      image: 'jc21/nginx-proxy-manager:latest'
      restart: always
      ports:
        - '80:80'
        - '81:81'
        - '443:443'
      environment:
        DB_SQLITE_FILE: "/data/database.sqlite"
        TZ: "America/New_York"
      volumes:
        - data:/data
        - /etc/letsencrypt:/etc/letsencrypt
   volumes:
    data:
   ```

   


