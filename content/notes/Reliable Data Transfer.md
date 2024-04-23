---
title: Reliable Data Transfer
enableToc: true
tags:
  - Networking
---
# Network Layer Imperfections
1. Segments can be **corrupted** by transmission errors
2. Segments can be **lost**
3. Segments can be **reordered** or **duplicated**

## Checksums
Simplest error detection scheme for corrupted or transmission errors is the checksum.

A Checksum can be based on different schemes. One scheme could be the arithmetic sum of all the bytes of a segment. Checksums are computed by the sender and attached with the segment. The receiver verifies it upon reception and can choose what to do if it is not valid. Often segments with invalid checksums are discarded. 

## Retransmission timers
Since the receiver sends an acknowledgement segment after receiving a data segment, the simplest solution to dealing with lost segments is a retransmission timer.

Once the sender sends a segment the retransmission timer is triggered. The timer should be greater than the round trip time. TCP sends an acknowledgement for every segment  so when the timer expires without an acknowledgement the segment is retransmitted.

![[files/Pasted image 20240409140828.png]]
### Limitations
If the data is received but the acknowledgement is lost then the sender will resend the data as a new segment meaning this segment is duplicated

To identify duplicates, the protocol associates an ID number with each segment called the sequence number. This way the receiver can identify duplicate ids.
![[files/Pasted image 20240409141017.png]]

# Pipelining
Applications may generate data at a higher rate then the network can transport. Processor speed > network I/O speed. 

Instead of waiting for acknowledgement of a message before transmitting the next one, the sender can keep transmitting messages without acknowledgement to make more efficient use of the processors time. 

Pipelining allows the sender to transmit segments at a higher rate but can cause the receiver to become overloaded.

## Sliding Window
The sliding window is the set of consecutive sequence numbers that the sender can use when transmitting segments without being forced to wait for an acknowledgment. At the beginning of a session, the sender and receiver agree on a sliding window size.

If the sliding window contains three segments the sender can thus transmit three segments before being forced to wait for an acknowledgment. The sliding window moves to the higher sequence numbers upon reception of acknowledgments. When the first acknowledgment (of segment 0) is received, it allows the sender to move its sliding window to the right, and sequence number 3 becomes available.

Unfortunately, segment losses do not disappear because a transport protocol is using a sliding window. To recover from segment losses, a sliding window protocol must define:

- A heuristic to detect segment losses.
- A retransmission strategy to retransmit the lost segments.


![[files/Pasted image 20240409141958.png]]
![[files/Pasted image 20240409142013.png]]
![[files/Pasted image 20240409142033.png]]
![[files/Pasted image 20240409142043.png]]

# Go-back-n
## Go-back-n Receiver
Intuitively, go-back-n receiver operates as follows:
1. It only accepts the segments that arrive in-sequence.
2. It discards any out-of-sequence segment that it receives.
3. When it receives a data segment, it always returns an acknowledgment containing the sequence number of the **last in-sequence segment** that it has received.

A **key advantage** of these cumulative acknowledgments is that it’s **easy to recover from the loss of an acknowledgment**.

Consider for example a go-back-n receiver that received segments 1, 2 and 3.
1. It sent acknowledgments for all three segments.
2. Unfortunately, acknowledgments of the first two were lost.
3. Thanks to the cumulative acknowledgments, the receiver receives the acknowledgment for the last segment and so it knows that all three have been correctly received.
![[files/Pasted image 20240409142642.png]]

## Go-back-n Sender
A go-back-n sender uses a sending buffer that can store an entire sliding window of segments.

- The segments are sent with a sending sliding window that we looked at in the last lesson.
- The sender must wait for an acknowledgment once its sending buffer is full.
- When a go-back-n sender receives an acknowledgment, it removes all the acknowledged segments from the sending buffer.

**Retransmission Timer**
A go-back-n sender uses a **retransmission timer** to detect segment losses. 
It maintains one retransmission timer per connection.

1. This timer is started when the first segment is sent.
2. When the go-back-n sender receives an acknowledgment, it restarts the retransmission timer, but only if any unacknowledged segments exist in its sending window.
3. When the retransmission timer expires, the go-back-n sender assumes that all of the unacknowledged segments currently stored in its sending buffer have been lost. It thus retransmits all the unacknowledged segments in the buffer and restarts its retransmission timer.

## Advantages of Go-back-n

The main advantage of go-back-n is that it can be easily implemented, and it can also provide good performance when only a few segments are lost. But when there are many losses, the performance of go-back-n quickly drops for two reasons:

- The go-back-n receiver does not accept out-of-sequence segments.
- The go-back-n sender retransmits all unacknowledged segments once it has detected a loss.

Since the go-back-n protocol does not accept out of order segments, it can waste a lot of bandwidth if segments are frequently lost.

The Selective Repeat protocol attempts to remedy this by accepting out of order packets and only retransmitting packets that are corrupted or lost in the network.

# Selective Repeat
- Uses a sliding window protocol just like go-back-n.
- The window size should be less than or equal to half the sequence numbers available. This avoids packets being identified incorrectly. Here’s an **example**: suppose the window size is greater than half the buffer size.
    - Segment ‘1’ is lost, hence the receiver expects a segment with sequence number 1 to be retransmitted.
    - Meanwhile, the window wraps around back to sequence number ‘1.’
    - The sender sends a new packet with sequence number 1 and the receiver perceives it to be the original one that it was expecting.
    
- Senders retransmit unacknowledged packets after a timeout or if a _NAK_ (_negative acknowledgment/not acknowledged_) is received.
- The receiver acknowledges all correct packets.
- The receiver stores correct packets until they can be delivered in order to the upper application layer.