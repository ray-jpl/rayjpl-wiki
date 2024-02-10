---
title: Redis
enableToc: true
tags:
  - System-Design
---
# Redis
Redis is a in-memory data structure store, used as a key-value database. 

Because it is in-memory it can leverage efficient low level data-structures including but not limited to:
- Linked Lists
- Sets
- Hash Tables
- Streams
- JSON
## Trade-offs:
**Advantages**
- High read/write throughput because its in-memory
	- Memory access is significantly faster than random disk I/O (DB)
- Low latency
**Disadvantages**
- Dataset cannot be larger than memory
## Uses
- Caching
- Messaging/Queues
- Real time leaderboards
- Session Storage
- Rate Limiters

## How to use Redis
- [Redis as an in-memory data structure quick start guide - Redis](https://redis.io/docs/get-started/data-store/)
- [Redis For Beginners](https://youtube.com/playlist?list=PL4cUxeGkcC9h3V2eqhi8rRdIDJshP-b4P&si=p1o-f7KsAREEqTPz)

# Sources
- [AWS - Redis](https://aws.amazon.com/redis/)
- [Top 5 Redis Use Cases - ByteByteGo](https://www.youtube.com/watch?v=a4yX7RUgTxI)
- [Why is single-threaded Redis so fast?](https://www.youtube.com/watch?v=5TRFpFBccQM)