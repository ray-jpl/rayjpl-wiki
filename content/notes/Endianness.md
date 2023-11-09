---
title: Endianness
enableToc: true
tags:
---
## Endianness
Refers to the order of bytes stored in memory
### Big Endian
A big-endian system stores the most significant byte of a word at the smallest memory address and the least significant byte at the largest.

### Little Endian
A Little-Endian system stores the most significant byte at the largest address and least significant at the smallest.
- Reversed order

e.g for the two byte hex number `b34f`. Little endian would look like this

| 0x100 | 0x101 |
| ----- | ----- |
| 4f    | b3    |

