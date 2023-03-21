---
title: "Kafka"
enableToc: true
tags:
- Kafka
---

## Event Streaming
"Event streaming is the practice of capturing data in real-time from event sources like databases, sensors, mobile devices, cloud services, and software applications in the form of streams of events; storing these event streams durably for later retrieval; manipulating, processing, and reacting to the event streams in real-time as well as retrospectively; and routing the event streams to different destination technologies as needed. Event streaming thus ensures a continuous flow and interpretation of data so that the right information is at the right place, at the right time."

Kafka is a distributed system consisting of servers and clients that communicate via a high-performance TCP network protocol. It can be deployed on hardware, virtual machines, and containers in on-premise as well as cloud environments.


## Concept
When an event occurs the producer creates a new record/event/message

### Producers
-   Receives updates and writes these 'records' into a queue
-   This queue is usually referred to as a Kafka Topic

### Topics
-   Messages in a Kafka topic are not delete when they are consumed/read
	-   Can use various policies to manage the messages
	-   Retention Policy
		-   Can set a rule to delete messages older than 24hrs
	
	-   Can also store older messages in Fault tolerant, persistent storage (Hard drive)
		-   Can be useful to recover previous messages if a Broker goes down

-   Topics can be organised into partitions
	-   This distributed placement of your data is very important for scalability because it allows client applications to both read and write the data from/to many brokers at the same time. When a new event is published to a topic, it is actually appended to one of the topic's partitions
	-   Kafka guarantees that any consumer of a given topic-partition will always read that partition's events in exactly the same order as they were written

### Broker
-   Brokers are the servers that these partitions run on
-   To make your data fault-tolerant and highly-available, every topic can be replicated, even across geo-regions or datacenters, so that there are always multiple brokers that have a copy of the data just in case things go wrong, you want to do maintenance on the brokers, and so on. A common production setting is a replication factor of 3

### Consumer
-   Consumers consume the messages in the queue
-   Listen for updates in real time
-   Consumers are very lightweight and should be able to create many without affecting performance
-   Use Offsets (pointers) to keep track of which latest message they have read

![kafka](files/kafka.png)


## References
- https://kafka.apache.org/intro
- [Kafka in 100 seconds](https://youtu.be/uvb00oaa3k8)
- [Apache Kafka in 6 minutes](https://youtu.be/Ch5VhJzaoaI)
- [Why is Kafka so Fast](https://www.youtube.com/watch?v=UNUz1-msbOM)
- [What is Kafka?](https://www.youtube.com/watch?v=aj9CDZm0Glc)