---
title: TCP-IP Model
enableToc: true
tags:
  - Networking
---
The protocols in this layer are clearly defined unlike the [[notes/OSI Model|OSI Model]]. 

## The layers of the TCP/IP Model
![[files/Pasted image 20240408121243.png]]
The layers in the TCP/IP stack largely perform the same functions as their counterparts in the OSI model, except that the application layer in the TCP/IP model encompasses the functionalities of the top three layers of the OSI model.

### Application Layer
Main purpose to enable end users to access the Internet
- Writing data off to the network in a format that is compliant with the protocol in use
- Reading data from end user
- Providing useful applications to end users
	- Browser, email agent, music streaming service etc
- Some applications also ensure that the data is in the correct format
- Error handling and recovery is also done by some applications
- **The Post Analogy**
	- Imagine you post a package across the world.
	- Presumably, the post system would hand it off to an airplane or ship to transport it across the world.
	- However, you would take it to the post office first to be shipped off. **Carrying the package to the post office** is what the application layer does in networks, except that **it carries messages to the transport layer**!

### Transport Layer
Responsibility is to take messages from an application and hand them to network layer and vice versa. The network layer transports messages from one end system to another but the transport layer delivers the message to and from the relevant application on an end system.

- Logical app to app deliver, transport layer makes it so that applications can address other applications on other end systems directly
- Segments data, divides data into segments/datagrams
- Allow multiple conversations, track each application connection separately which can allow multiple conversations at once
- Multiplexing and demultiplexing data. Ensure that data reaches the relevant application within an end system. If multiple packets get sent to one host then each will end up at the correct application.
#### Transport Layer Protocols
Transport layer has two prominent protocols Transmission Control Protocol (TCP) and User Datagram protocol (UDP).

- [[notes/Multiplexing|Multiplexing]]
- [[notes/Network Congestion|Network Congestion]]