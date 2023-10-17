---
title: CPU Registers
enableToc: true
tags:
  - OS
---
## Registers
Registers are a type of computer memory built directly into the processor that is used to store and manipulate data during the execution of instructions. Registers may hold instructions, a storage address or any kind of data. 

A register is composed of multiple flip-flops, electronic circuits capable of storing a single bit of information. By combining multiple flip-flops, registers can store/represent larger binary values.

Registers also contain control logic which allow it to coordinate the flow of data and instructions within the CPU.


### Types of Registers
- **Program Counter (PC)**: Keeps track of the memory address of the next instruction to be executed
- Instruction Register (IR): Contains current instruction being executed
- Accumulator (ACC): General purpose register used for arithmetic and logical operations. Store intermediate results during calculations
- General Purpose Registers (R0, R1, R2 ...): Store data during calculations and data manipulation
- Address Registers (AR): Store memory addresses for data access or for transferring data between different memory locations
- Stack Pointer (SP): Points to the top of the stack, a region of memory used for temporary storage during function calls and other operations. 
- Data Registers (DR): Store data fetched from memory or obtained from I/O operations
- Status/ Flags Register (SR): Contains the individual buts that indicate the outcome of operations such as carry, overflow, zero result and others. 
- Control Registers (CR): Handles settings relating to CPU operation such as interrupt handling, memory management and system configurations.