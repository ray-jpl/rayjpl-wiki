---
title: OSI Model
enableToc: true
tags:
  - Networking
---
# The OSI Model
The OSI model provides a standard for different computer systems to communicate with each other. However, OSI is a **theoretical model** and works very well for teaching purposes, but it’s not practically used. [[notes/TCP-IP Model|TCP/IP]] is used practically. 

## The Layers of the OSI Model
![[files/Pasted image 20240408114814.png]]

### Application Layer
- End users interact with the application layer
- Where most end-user applications such as web browsing and email live
- Where the outgoing message starts its journey so it provides data for the layer below

### Presentation
- Presents data in a way that can be understood and displayed by the application layer
	- **Encoding** is an example. The underlying layers might use different character encoding compared to the one used by the application layer.
- Encryption is also done at this layer
- End-to-end compression: the presentation layer might also implement end to end compression to reduce traffic in the network

### Session
- Responsibility is to take services of the transport layer and build a service on top that manages user sessions
- A session is an exchange of information between local apps and remote services on the other end systems

### Transport Layer
- Since the application, presentation and session layers may be handing off large chunks of data, the transport layer segments it into smaller chunks
	- These are called Datagrams or segments depending on the protocol used
- Sometimes additional information is required to transmit the segment/datagram reliably.
	- Checksum - ensure message is correctly delivered without corruption
	- Header - Information at the start of the datagram
	- Trailer - Information at the end of the datagram

### Network Layer
- Network layer messages are termed as **packets**. 
- Facilitate the transportation of packets from one end system to another
- Routing protocols are apps that run on the network and exchange messages with each other to develop information that helps them route transport layer messages
	- Help determine the best routes that a message should take
- Load balancing

### Data Link Layer
- Allows directly connected hosts to communicate
- Encapsulates packets for transmission across a single link
- Resolve transmission conflicts - when two end systems send a message at the same time across one singular link
- Handles addressing
- Multiplexing and Demultiplexing
	- Multiple data links can be multiplexed into something that appears like one to integrate their bandwidths

### Physical Layer
- Consists largely of hardware
- Provides medium to transmit data
- Transmits bits, not logical packets, datagrams or segments


## Example
![[files/Pasted image 20240408120154.png]]
1. Application layer writes out streams of data to presentation layer
2. Presentation hands it off to session layer then to transport layer
3. Transport layer segments this data into datagrams
4. Network layer turns these datagrams/segments into packets
5. Physical layer carries each packet as bits to other end system
6. Reverse process happens from here to convert the bits back to application layer