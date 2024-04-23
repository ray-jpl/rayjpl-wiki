---
title: Database Scaling
enableToc: true
tags:
  - System-Design
---
# Data consistency
A system with data consistency strives for every service to see the same data at the same time. This is simple when you have one database but when you have multiple replica databases it becomes more difficult.

There are two main types of consistency. **Strong Consistency** and **Eventual Consistency**.
## Strong Consistency
Strong consistency means that every read request for the data **must** return the most up to date value. 
Typically used in applications where transactions occur to ensure data integrity and fairness. 

There are some strategies to achieve strong consistency
- **Master Database**
	- Designate one of the database as the primary database which is the only database that accepts writes. All other databases are read replicas. 
	- When data is written, updates are applied **synchronously** to all other replicas
		- While an update is occurring read/write requests will be **blocked** until the update is propagated across all replicas. This ensures that read operations only see the latest state of data.
			- This guarantees strong consistency but can reduce availability and latency of the system. Can also cause read/write timeouts
		- An alternative to that is to send all read/writes to the primary DB as it is guaranteed to be up to date and requests will not be blocked. However can cause overload to the server. 
- **Two Phase Commit**
	- The process involves the following steps: 
		- **Prepare phase:** The coordinating node (usually the primary replica) sends a "prepare" message to all participant nodes (secondary replicas), asking them to prepare to commit the transaction. 
		- **Commit phase:** If all participants successfully prepare, the coordinating node sends a "commit" message to all participants, and they apply the updates. If any participant fails, the coordinating node sends a "rollback" message, and the participants undo the changes.
## Eventual Consistency
Eventual consistency is when a data value is updated, eventually all the read requests will return the most up to date value. Allows for greater availability and scalability in distributed systems by relaxing the synchronization requirements between nodes.
# Master-slave replication
Pattern where only one master database is responsible for writes while remainder are read replicas. Same pattern mentioned in [[#Strong Consistency]]. If the master goes offline, the system can continue to operate in read-only mode until a slave is promoted to a master or a new master is provisioned.
**Disadvantages**
- Potential for loss of data if the master fails before any newly written data can be replicated to other nodes.
- Writes are replayed to the read replicas. If there are a lot of writes, the read replicas can get bogged down with replaying writes and can't do as many reads.
- The more read slaves, the more you have to replicate, which leads to greater replication lag.
- On some systems, writing to the master can spawn multiple threads to write in parallel, whereas read replicas only support writing sequentially with a single thread.
- Replication adds more hardware and additional complexity.
## Master-Master replication
Master-master replication is where multiple databases have read/write permissions. If either master goes down, the system can continue to operate with both reads and writes.

In addition to the master-slave replication disadvantages we also have the following disadvantages.
**Disadvantages**
- Need a load balancer or make changes to your application logic to determine where to write.
- Most master-master systems are either loosely consistent (violating ACID) or have increased write latency due to synchronization.
- Conflict resolution comes more into play as more write nodes are added and as latency increases.
# Database Sharding
Sharding is a horizontal scaling technique that separates a single database into smaller parts called shards, where each shard shares the same schema but contain a different range of data.  E.g if we were sorting by name and had two databases, we could say Shard 1 is responsible for all names starting with A-M and Shard 2 is responsible for N-Z.

The data on each shard is unique. Anytime data is accessed a hash function is used to find the corresponding shard similar to a hashmap.  E.g if we shard a database based on user id and have 4 total shards we can use a hash function such as $user\_id \  \% \  4$ to get the corresponding shard.   

However sharding is not a perfect solution
**Resharding Data:** 
- Resharding data is needed when a single shard can no longer hold more data. Certain shards may experience shard exhaustion faster than others due to uneven data distribution. 
- To reshard data the hash function needs to be updated to distribute the data among shards more evenly. Updating the sharding function means that some existing data will need to be moved in order to match the hash function. A common technique to solve this is [[notes/Consistent Hashing|Consistent Hashing]].
**Celebrity Problem:**
- Excessive access to the same shard can cause server overload. For a social application if many celebrities are on the same shard then that shard may be overwhelmed with read operations. Celebrities may need their own shard each.
**Join and de-normalization**:
- Once a database is sharded it is harder to perform join operations across database shards. A common workaround is to de-normalise the database so that queries can be performed in a single table.

# References
- [Consistency Patterns - Neo Kim](https://systemdesign.one/consistency-patterns/)
- [Data Consistency and Tradeoffs in Distributed Systems - Gaurav Sen](https://www.youtube.com/watch?v=m4q7VkgDWrM)