---
title: Event Loop
enableToc: true
tags:
  - JavaScript
---
# Event Loop
The call stack is a mechanism for keeping track of the execution context of a script. Whenever a function is called, JavaScript pushes it onto the call stack. When that function completes, JavaScript pops it off the stack, allowing the execution to continue with the next item in the stack.

JavaScript is a single threaded programming language and therefore it can only execute the function currently at the top of the stack. However when a function is processing a blocking event like a network request or file i/o would prevent other functions to be added to the call stack.

In the browser, asynchronous events like network requests are handed off to a web apis. Once those events are finished they are moved into the callback queue. The callback functions are only pushed on top of the JavaScript callstack when the callstack is empty. This way the thread is not blocked by asynchronous tasks. 

![[files/Pasted image 20240312230344.png]]
The Node.js event loops operates with the same concept. Quote from the Node.js website
"*Each phase has a FIFO queue of callbacks to execute. While each phase is special in its own way, generally, when the event loop enters a given phase, it will perform any operations specific to that phase, then execute callbacks in that phase's queue until the queue has been exhausted or the maximum number of callbacks has executed. When the queue has been exhausted or the callback limit is reached, the event loop will move to the next phase, and so on.*"

![[files/Pasted image 20240312230908.png]]

![[files/Pasted image 20240312231143.png]]
# References
- [What the heck is the event loop anyway?](https://www.youtube.com/watch?v=8aGhZQkoFbQ)
- [Everything you need to know about Node.js Event Loop](https://www.youtube.com/watch?v=PNa9OMajw9w)
- https://witkesam.medium.com/solving-the-blocked-event-loop-in-node-js-abb6cac281a7
- https://medium.com/the-node-js-collection/what-you-should-know-to-really-understand-the-node-js-event-loop-and-its-metrics-c4907b19da4c
- https://nodejs.org/en/learn/asynchronous-work/event-loop-timers-and-nexttick
