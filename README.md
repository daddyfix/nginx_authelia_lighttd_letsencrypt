# Self Hosting Domain Authetication Tutorial on Linux

Took me a while to put all these peices together. Hopefully someone can use this small tutorial

## Hardware and OS

+ Linux 5.15.0-113-generic x86_64 GNU/Linux
+ Ubuntu 22.04 (jammy)
  
## Software
1. [Nginx Proxy Manager (NPM)](https://nginxproxymanager.com/)
    This project comes as a pre-built docker image that enables you to easily forward to your websites running at home or otherwise, including free SSL, without having to know too much about Nginx or Letsencrypt.
    
2. [Authelia](https://www.authelia.com/) (Standalone Daemon Service)
   Authelia is an open-source authentication and authorization server and portal fulfilling the identity and access management (IAM) role of information security in providing multi-factor authentication and single sign-on (SSO) for your applications via a web portal. It acts as a companion for common reverse proxies.

## 

Tutorial on how to install Nginx-Proxy-Manager, Authelia, Lighttpd, Letsencrypt for self hosting domains
