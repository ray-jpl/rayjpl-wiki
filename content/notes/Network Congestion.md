---
title: Network Congestion
enableToc: true
tags:
  - Networking
---
# What is Congestion
When more packets than the network has bandwidth for are sent through, some of them start getting dropped and others get delayed. 

# How to fix Congestion
Congestion physically occurs at the network layer (in routers) but it is mainly caused by the transport layer sending too much data at once.

How the transport layer controls congestion:
- Send packets at a slower rate in response to congestion
- The ‘slower rate’ is still fast enough to make efficient use of the available capacity,
- Keep track of changes in traffic to adjust rates accordingly

# Bandwidth Allocation Principles
## Allocation Basis
**Should bandwidth be allocated to each host or to each _connection_ made by a host?**
Usually bandwidth is allocated per connection.

- Not all hosts are equal. Some can send and receive higher data rates than others.
- Allocating bandwidth equally to all hosts then some would not be able to use bandwidth to full capactiy and some would not have enough bandwidth.
	- An Internet enabled doorbell would have too much bandwidth and a busy server would have too little if both had the same bandwidth.
- Per connection allocation can be exploited by hosts opening multiple connections to the same end system

## Bursts of traffic
Dividing bandwidth equally across multiple end systems may seem to be most efficient but in a real setting each end system would probably not use all bandwidth. Real traffic can come in bursts and a large burst in traffic may result in more than the allocated bandwidth to be needed causing congestion and subsequent drop in performance. Therefore bandwidth cannot be divided equally amongst end systems. 

## Transmission Threshold
![[files/Pasted image 20240409120834.png]]

Routers have a set input and output limit. When these limits are exceeded the excess packets are placed in a queue, when the queue becomes full the router cannot store anymore packets and that is how packets get dropped.

As the **average** transmission rate approaches the service rate, the queue may start to fill up. As the queue fills up the delay increases exponentially until we reach max capacity. Once max capacity is reached the packets will start getting dropped.