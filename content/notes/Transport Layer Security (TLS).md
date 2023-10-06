---
title: TLS
enableToc: true
tags:
  - TLS
  - SSL
  - Networking
---
## What is TLS
TLS evolved from [[notes/Secure Socket Layer (SSL)|SSL]] and changed it name however people still use the terms interchangeably. Functionally they serve the same purpose which is to encrypt web requests.

## TLS Handshake
When a user navigates to a website that uses TLS, the process begins

- The user's device and webserver specify which version of TLS they are using.
- Decide on which cipher suite to use
- Authenticate the identity of the server using the server's TLS certificate
- Generate session keys for encrypting messages between them after the handshake is complete

A full description of the steps are here [TLS Handshake](https://www.cloudflare.com/learning/ssl/what-happens-in-a-tls-handshake/)
