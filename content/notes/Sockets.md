---
title: Sockets
enableToc: true
tags:
  - Networking
---
## What is a socket
A socket is a way to speak to other programs using standard Unix file descriptors.
> When Unix programs do any sort of I/O, they do it by reading or writing to a file descriptor. A file descriptor is simply an integer associated with an open file. But that file can be a network connection, a FIFO, a pipe, a terminal, a real on-the-disk file, or just about anything else. Everything in Unix _is_ a file! So when you want to communicate with another program over the Internet you’re gonna do it through a file descriptor.

### Types of Internet Sockets
#### Stream Sockets
- *SOCK_STREAM*
- TCP (Transmission Control Protocol)
- Reliable **two-way** connected communication streams
- Data arrives sequentially and error free. 
#### Datagram Sockets
- *SOCK_DGRAM*
- UDP (User Datagram Protocol)
- Unreliable. The packet may arrive and they may arrive out of order.
- Sometimes referred to as 'connectionless sockets
	- Do not need to maintain an open connection with a client
- Trade-off of using an unreliable protocol is speed.
	- Use UDP if speed is important and the order of packets and potentially dropped packets dont matter.
#### Raw Sockets
- *SOCK_RAW*
- A raw socket allow user to implement it's own Transport Layer Protocol above internet (IP) level . 
	- Implementation is responsible for creating and parsing transport level headers and logic behind it.
	- Same level as TCP/UDP in [[#Data Encapsulation]]

### Data Encapsulation
![[files/Pasted image 20231109230309.png]]
Data packet is encapsulated in a header by the first protocol (TFTP in this case). Then the entire thing including the TFTP headers are encapsulated in the next protocol (UDP in this case) and so on. 

When a computer receives the packet, the hardware stripts the Ethernet Protocol. 
The OS kernel strips the IP and UDP protocols.
The TFTP program strips the TFTP headers and finally has the data. 

## Byte Order
Networks store bytes in *Network Byte Order* or [[notes/Endianness#Big Endian|Big-Endian]]. 
The byte order your machine uses is referred to as *Host Byte Order*. Some computers may store bytes in reverse, [[notes/Endianness#Little Endian|Little-Endian]] or it might be Big Endian as it is dependent on the machines architecture. 
- Intel microprocessors are little endian

Hence never assume the Host Byte Order, there are functions to convert to Network host order. 
- Code will also be portable if using the function otherwise code will only work on specific machines

Can convert `short` (two bytes) and `long` (four bytes) numbers.  
> Say you want to convert a `short` from Host Byte Order to Network Byte Order. Start with “h” for “host”, follow it with “to”, then “n” for “network”, and “s” for “short”: h-to-n-s, or `htons()` (read: “Host to Network Short”).

|Function|Description|
|---|---|
|`htons()`|host `to` network short|
|`htonl()`|host `to` network long|
|`ntohs()`|network `to` host short|
|`ntohl()`|network `to` host long|


## References
- [Beej's Guide to Network Programming](https://beej.us/guide/bgnet/html/)
- https://docs.python.org/3/howto/sockets.html