---
title: Multiplexing
enableToc: true
tags:
  - Networking
---
# What is Multiplexing and Demultiplexing
End systems can run a variety of applications at the same time so how does the end system know which process to deliver packets to. 

Demultiplexing is the process of delivering the packets to the correct applications from one data stream. Multiplexing allows messages to be sent to more than one destination host. 
Can model it like a highway between two cities. Cars coming from different suburbs in city A all merge onto one highway. They all have a different destination in city B and need to get off at different off ramps. Similarly you don't want the server sending packets to your machine for the browser application to be routed to your Discord/Skype application. 

[[notes/Sockets|Sockets]] are gateways between an application and the network. If an application wants to send something over to the network it will write the message to its socket. The transport layer is responsible for labelling packets with the port number of the application a message is from and the one it is addressed to. 

# Multiplexing and Demultiplexing in UDP
- When a datagram is sent from an application, the port number of the source and destination application is appended to it in the UDP protocol header.
- When the datagram is received it will send the datagram to the relevant application socket based on the destination port number.

## Port assignment in UDP
- Common to let the port on client side to be assigned dynamically instead of choosing a particular port
	- Since client initiates connection to the server it must know the port number of the application on the server but the server does not need to know the clients port number in advance. 
	- When the client sends its first datagram it will contain the client port number which the server can use to send datagrams back to the client


# References
- [Transport Layer multiplexing and demultiplexing](https://www.youtube.com/watch?v=CekW6ipRrGA)