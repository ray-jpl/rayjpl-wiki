---
title: SSL
enableToc: true
tags:
  - SSL
  - SSL
  - Certificate
  - TLS
  - Networking
---
### What is SSL?
Secure Socket Layer (SSL) is an encryption-based security protocol. It is the predecessor to [[notes/Transport Layer Security (TLS)|TLS]]. 
A website that uses SSL/TLS has HTTPS in its URL instead of HTTP.

SSL encrypts data that is transmitted across the web. The data is also signed in order to provide data integrity, verifying that the data is not tampered with before it reaches its destination. SSL also initiates an authentication [[notes/Transport Layer Security (TLS)#TLS Handshake|handshake]] between two devices to ensure that both devices are really who they claim to be. 

SSL has not been updated since 1996 and now deprecated as there are several known security vulnerabilities. TLS is its successor, however there is sometimes confusion as TLS is still commonly referred to as 'SSL Encryption'. 


## What is an SSL Certificate
SSL can only be implemented by websites that have an SSL/TLS certificate. It allows websites to use the HTTPS protocol. 

SSL certificates are a data file hosted on a websites origin server. These certificates are sent to any devices that request to load the webpage. On chrome you can view an SSL certificate by clicking on the padlock icon next to the URL. 

The certificate contains:
- The domain name that the certificate was issued for
- Which person, organization, or device it was issued to
- Which certificate authority(CA) issued it
- The certificate authority's digital signature
- Associated subdomains
- Issue date of the certificate
- Expiration date of the certificate
- The public key (the private key is kept secret)

The public key is used to encrypt data before it is sent to the webserver. The webserver can decrypt this information using a private key. 

## Sources
- https://www.cloudflare.com/learning/ssl/what-is-ssl/
- https://www.cloudflare.com/learning/ssl/what-is-an-ssl-certificate/