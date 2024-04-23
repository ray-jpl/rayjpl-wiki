---
title: Typing a URL in the browser
enableToc: true
tags:
---
# What happens when you type a URL into the browser
Websites are a collections of HTML, CSS and JavaScript files and the browser uses these files to display the site to you. These files are stored on another computer on the internet called a server. 

To get these files we need to find the right server. Every device connected to the internet has a unique IP address which is denoted by four numbered parts,  e.g "203.0.113.0". IP addresses arent very human friendly as it would be difficult to remember which IPs corresponded to different websites. The Domain Name System(DNS) maps these IP addresses to a domain name. 
## Typing URL into browser
Once you have typed in the URL into the browser and pressed enter, the browser will then do a DNS lookup to find the IP address of the server. To remain fast, the IP address is cached at multiple different levels. For frequently visited websites such as google.com this will improve performance. First the browser may have already cached the result, then the operating system, local network cache at your router and then a DNS server cache at your ISP. If your ISP does not have the website cached then it will perform a DNS recursive lookup which queries other DNS servers to see if they have a cache hit. It performs the search recursively, so if those first set of servers do not have the IP then they query other DNS servers.

## Establish TCP Connection
Once the browser has an IP address it tries to establish a connection with the server. [[notes/TCP-IP Model|TCP Connection]] is used for its reliability over UDP, it ensures that all data packets are received and not corrupted.   

The TCP connection follows a 3-step handshake process. 
1. The client sends a SYN packet with a randomly generated sequence number(e.g 1000). This sequence number is used for reliable data transfer and maintaining the order of the packets. The SYN packet also contains other flags and options such as the Maximum Segment Size(MSS) which indicates the maximum amount of data the client can receive in a single TCP segment. 
2. Once the server receives the SYN packet it responds with a SYN-ACK packet. This packet contains the servers own initial sequence number (e.g 2000) which is different to the clients' sequence number. The server acknowledges the clients packet by incrementing the clients sequence number by 1. The packet also included the servers options and MSS. 
3. The client receives the SYN-ACK packet and responds with an ACK packet. The client increments the servers initial sequence number by 1 and the handshake is complete. 

The handshake process ensures that the server and client are ready to communicate and also negotiate on various parameters such as initial sequence numbers and MSS.

## HTTP Requests
Once the connection is established the browser can then send a HTTP request to request the contents of the page. The server then processes the HTTP request and returns a HTTP response and the browser renders the page accordingly.

# Resources
- [What happens when you type a URL into the browser - AWS](https://aws.amazon.com/blogs/mobile/what-happens-when-you-type-a-url-into-your-browser/#:~:text=and%20press%20Enter-,Browser%20looks%20up%20IP%20address%20for%20the%20domain,and%20sends%20back%20a%20response)
