---
title: "Proxy"
enableToc: true
tags:
- Proxy
---
## What is a proxy server
A proxy server is an intermediate server separating end users and the website they are browsing. This is to not expose the internal network to the public internet. When you send a web request, the request is sent to the proxy server and the proxy server will then make a request to the webserver on your behalf. 

The proxy server can change your IP so that the webserver doesn't know where you are, encrypt data so it is unreadable in transit or block access to certain webpages based on IP address. 

The proxy server can act as a firewall, web filter and/or cache data for common requests. 

A proxy server is sometimes referred to as a forward proxy. Its to describe a server that sits in front of client machines and communicates with web servers on behalf of those clients. It is so that an origin server never directly interacts with the client.
#### Common use cases
- Control/monitor internet usage of employees/children
- Bandwidth savings and improved speed through caching
	- If hundreds of people want to access a specific webpage through a proxy server, the proxy server sends one request to the URL and sends the same response back to the hundreds of requests. This saves bandwidth and improves performance
- Privacy
	- Proxy servers can hide or alter identifying information in web requests.

