---
title: Garbage Collection
enableToc: true
tags:
---
# What is Garbage Collection
Garbage collection in programming languages is a form of memory management. Garbage collection reclaims memory that has been allocated but is no longer referenced in the program. 

High level programming languages like Python and Java have garbage collection built in although they may have different implementations. For low level languages like C/C++ manually allocation and deallocating memory is required. 

The advantages of Garbage Collection is it helps avoid memory errors such as 
- Freeing memory which still has pointers referencing it. Dereferencing these pointers can cause unexpected behaviour as the data in that memory may have be reassigned to something else. 
- Freeing memory twice 
- Memory Leaks

The main disadvantage of GC is performance. The process will require extra computing resources to determine which areas of memory can be freed.
