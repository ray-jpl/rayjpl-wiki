---
title: System Design
enableToc: true
tags:
  - "#System-Design"
---
# Notes
- [[notes/Redis|Redis]]
- [[notes/Reverse Proxy|Reverse Proxy]]
- [[notes/Event Driven Architecture|Event Driven Architecture]]
- [[notes/Database Scaling|Database Scaling]]
- [[notes/Database Internals|Database Internals]]
# Resources
- [Hello Interview](https://www.hellointerview.com/learn/system-design/in-a-hurry/introduction)
- [System Design Primer - donnemartin](https://github.com/donnemartin/system-design-primer)
- [Awesome System Desgin - madd86](https://github.com/madd86/awesome-system-design)
- [System Design 101 - ByteByteGo](https://github.com/ByteByteGoHq/system-design-101)

# How to approach system design interviews
Follow a framework for system design interviews as there is not much time to get through everything, its easy to waste time on things that don't matter and can make it hard for the interviewer to follow.
Most system design interviews will be 60mins, 10mins of that will be introductions and asking questions at the end so we realistically have maybe 45-50mins.
## 1. Outline use cases, constraints and assumptions
Gather requirements and scope the problem. Ask questions to clarify use cases and constraints. Discuss assumptions. Narrow these down to functional and non functional requirements. 

> Task should take around 5-10mins at most. Important to clarify what is important before jumping in but don't spend too much time here and be decisive on what is important. 

- **Try to suggest features that you know you can answer**
	- Try to just stick to core functionality and ask if that is ok or if they want more features
- Who is going to use it?
- How are they going to use it?
- How many users are there?
- What does the system do?
	- Constraints of the system

> Important to clarify usage. E.g a chat application is vague. Whatsapp is mainly 1 on 1 texting while something like Discord is more group chat. 
### Functional Requirements
- Convert how the system being used into some functional requirements/APIs
	- Try to keep in mind the noun and verbs discussed previously
		- "The system has to **count *video view events***"
	- On the video we can count video views or any video event

### Non-functional Requirements
- Non-functional are attributes that are important. Try to prioritise at least two.
	- Most interviews scalability and performance are the most applicable
	- Ask yourself if data consistency is important for read/writes. For some questions its easy to rule out if it is very important

**Scalability**
- Scalability is the measure of a system's ability to increase or decrease in performance and cost in response to changes in application and system processing demands.

**Performance**
- Performance is an indication of the responsiveness of a system to execute any action within a given time interval
- Usually related to words like latency
- Throughput is number of actions per unit of time

**Availability**
- Availability is the percentage of time in a given period that a system is available to perform its task and function under normal conditions. **One way to look at is how resistant a system is to failures**.
- Solution: Eliminate single points of failure
	- Redundancy
		- Redundant data means redundant databases
		- Redundant load balancers
	- Passive Redundancy
		- Multiple components at a given layer in your system

**Fault Tolerant**
- Similar to availability
	- Fault tolerance requires full hardware redundancy
		- Several systems run in parallel
		- If main system fails then the another can take over

**Consistency**
- Eventual Consistency
	- Website data is replicated across multiple data centres
		- Changes to the data in one of the data centres does not immediately change all of them
		- The change is propagated to the other servers and updated in the background
		- Eventually the data will be the same across all datacentres
- Strict Consistency
	- Strict consistency states that for any incoming write operation, once a write is acknowledged to the client, the updated value is visible on read from any replicated node (server) in the system. This effectively means that  all readers are blocked until replication of the new data to all the nodes are complete.

## 2. Capacity Estimation
- How much data do we expect to handle?
- How many requests per second do we expect?
- What is the expected read to write ratio?
 > This should be a quick calculation to get the order of magnitude correct. Should spend around 2 mins here. 
 
Do some back of the envelope calculations for things like storage size. Perhaps some calculations  based on Read/Write ratio. This section starts to inform you of where you should focus your design on.

During this section you may need to list what data is important to get a capacity estimate. You can start to create an idea of if you're going to use an SQL or NoSQL database.


## 3. High Level design and buy in
Have a high level overview of the design, discuss with the interviewer until you get to a state which is acceptable to them. High level design is focussing on satisfying all the functional requirements and getting a working system.

The headings here are the suggested order to follow in this section as it has a natural progression. However your interviewer may direct the order you go through these. 

> Lots of different sections to accomplish here, should take maybe 20mins
### API Design
Translate your functional requirements into API endpoints
Follow RESTful conventions and define input and output parameters.

Level of detail you should provide varies here. There may be algorithms or functions that you may need to explain here. E.g sorting algo, hash function. Some interviews may ask you to write some pseudocode of what the function might look like.

![[files/Pasted image 20240408220424.png]]

>  Make sure the APIs listed cover **ONLY** the functional requirements. Also make sure you **don't** have APIs that don't address any functional requirements

Some designs may call for a two-way communication between client and server. In this scenario a web socket is a common solution. Websockets are stateful so it is difficult to operate at scale, would need to expand in deep dive section.

### High Level Diagram
Create a rough diagram of the services and overall design of the system. This shows how the core components interact/relate to each other. 

You can take a top down approach to make sure you don't miss anything. Most designs will follow this basic flow
Client > Load Balancer > Services > Persistent Data Layer/Cache
Now you can expand on the data layer and break it up into databases, object stores, cache etc.

> In this section try not to go too much detail while creating the diagram to avoid digging yourself into a hole

### Data Model
Now you can discuss the data model. Topics such as data access patterns, database schema.
- At scale this may impact the performance of your design
- Perhaps discuss specific databases to choose and indexing options

> If the data model is crucial to one of the non-functional requirements (like consistency) then optimising and scaling it belongs more to the deep dive section

Once complete then make sure the design is complete end to end.

## Design Deep Dive
Here is where you identify areas which could be problematic and discuss solutions and tradeoffs. E.g bottlenecks, abnormal cases of high reads/writes. Discuss where problems are present and ask the interviewer which one they want to focus on. You can usually find problems which are related to the non-functional requirements you listed.

> This section should take around 15-20mins. Might only have time to delve into one problem, depends how deep the interviewer wants to test you. Should only have time for 2-3 issues. The more senior the position, the more important this section is.

The framework to approach this section:
1. Articulate a problem
2. Provide at least 2 solutions
3. Discuss trade offs of each solution
## Summarise Design
- Summarise design
- Focus on features that are specific to this design
- Don't spend long here

# References
- [System Design Interview - Step by Step Guide](https://www.youtube.com/watch?v=i7twT3x5yv8)