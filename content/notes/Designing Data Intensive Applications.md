---
title: "Designing Data Intensive Applications"
enableToc: true
tags:
- 
---
These are just notes I've taken on the book "Designing Data Intensive Applications  - Martin Kleppmann"
## Main Concerns
- Reliability
- Scalability
- Maintainability
#### Reliability
The system should continue to work correctly even in the face of adversity

Things that can go wrong are called *faults* and systems that anticipate faults are *fault-tolerant* or *resilient*.

**Hardware Faults**
Things such as hard disk failure, faults RAM and blackouts can happen and cause system failure. A usual response to this is to add redundancy to individual components to reduce failure rate. This way redundant components can continue to work while the broken one is replaced. 

Increased data volume and computing demands has lead to more applications uses a larger number of machines which proportionally increases the rate of hardware faults. Hence there is a move towards systems that can tolerate the loss of entire machines using software fault-tolerance techniques in addition to hardware redundancy. 

**Software Errors**
Another class of fault is a systematic error which are harder to anticipate. 
- Software bugs that cause every instance of an application to crash when a certain event occurs
- A runaway processes that continually use up a shared resource such as CPU, memory, disk or network bandwidth.
- Cascading failures where a fault in one component triggers a fault in another and so on
These software errors often lay dormant until they are triggered by unusual circumstances. 

There is no quick solution to resolving systematic faults in software. 
Some things that may help:
- Carefully thinking about assumptions and interactions in the system
- Thorough testing
- Process Isolation
- Allowing processes to crash and restart
- Measuring, monitoring and analysing system behaviour in prod

**Human Error**
Humans are known to be unreliable and the operators who keep systems running are also human
- Design systems to minimize opportunities for error.
- Decouple the places where people make the most mistakes from the places where they can cause failure. e.g providing sandbox environments to experiment in without affecting real users
- Test thoroughly at all levels. from [[notes/Unit Testing|Unit Testing]], [[notes/Integration Testing|Integration Testing]] and manual tests. 
- Allow quick and easy recovery from human errors to minimise the impact in the case of a failure.
- Set up detailed and clear monitoring, such as performance metrics and error rates. Monitoring can show us early warning signals and can be invaluable at diagnosing issues
- Implement good management practices and training.

#### Scalability
As the system grows in data volume, traffic or complexity, there should be reasonable ways of dealing with that growth.
**Describing Load**
First we need to succinctly describe the current load on the system and then we can discuss growth. Load can be described with load parameters. These parameters are 
**Describing Performance**

#### Maintainability
Over time, many different people will work on the system and they should all be able to work on it productively.