---
title: Sockets
enableToc: true
tags:
  - Networking
---
## What is a socket
A socket is a way to speak to other programs using standard Unix file descriptors.
> When Unix programs do any sort of I/O, they do it by reading or writing to a file descriptor. A file descriptor is simply an integer associated with an open file. But that file can be a network connection, a FIFO, a pipe, a terminal, a real on-the-disk file, or just about anything else. Everything in Unix _is_ a file! So when you want to communicate with another program over the Internet you’re gonna do it through a file descriptor.

### Two Types of Internet Sockets
#### Stream Sockets
#### Datagram Sockets

## References
- [Beej's Guide to Network Programming](https://beej.us/guide/bgnet/html/)
- https://docs.python.org/3/howto/sockets.html