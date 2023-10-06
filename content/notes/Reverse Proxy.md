---
title: "Reverse Proxy"
enableToc: true
tags:
- Reverse Proxy
- Proxy
---
## What is a reverse proxy
A reverse proxy is a type of [[notes/Proxy|Proxy Server]] that typically sites behind the firewall in a private network and directs requests to the appropriate backend server. Provides an additional level of abstraction and control to ensure the smooth flow of network traffic

A reverse proxy is different to a forward proxy. It sits in front of webs servers and intercepts incoming traffic to prevent any client from directly communicating with the origin server.
####  Common use cases
 - Load Balancing
	 - Distribute traffic evenly across a group of backend servers
 - Web Acceleration
	 - Cache commonly requested content
	 - Compress inbound/outbound data
 - Security
	 - Protect backend servers from attacks
 - SSL Encryption
	 - Encrypting and decrypting SSL or TLS communications can be computationally expensive for an origin server. Can offload these tasks to the proxy to free up resources.

## Sources
- https://www.cloudflare.com/learning/cdn/glossary/reverse-proxy/