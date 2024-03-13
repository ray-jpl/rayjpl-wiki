---
title: What is Java JVM
enableToc: true
tags:
  - Java
  - JVM
---
# What is the JVM
 The JVM serves as an abstraction layer between the Java code and the underlying hardware. When a Java program is compiled, it generates bytecode, which is then interpreted by the JVM at runtime. It follows the concept of  **WORA (_Write Once Run Anywhere_)**, where code can be written once and be used on any hardware that has a compatible JVM. 

First it might be useful to differentiate the difference between the JDK, JRE and JVM.

## JDK
The Java Development Kit (JDK) provides the tools necessary to write and develop Java programs. This usually contains tools like the compiler which converts Java code(.java) to Java byte code (.class), debugger and the runtime environment which is what you use to run the code (JRE in this case). 

## JRE
The Java Runtime Environment (JRE) contains sets of libraries and files that the JVM uses at runtime. It has a physical location on disk. The JRE is platform dependant as it needs to have the appropriate libraries to access the correct native OS methods. 

The JRE can be used to run Java byte code, the JDK is not required. 

![[files/Pasted image 20240313210712.png]]

## JVM
The JVM can be thought of as 3 seperate systems: Class Loader, JVM Memory and Execution Engine. 
The Java is both a [compiled and interpreted language](https://www.freecodecamp.org/news/compiled-versus-interpreted-languages/). The Java code is **compiled** into byte code and that byte code is **interpreted** by the JVM.


![[files/Pasted image 20240313222702.png]]
### Class Loader
The class loader is responsible for loading the compiled byte code classes into the JVM. This includes the compiled classes from the application and also the standard library which includes things like Strings, Collections etc.

Linking involves verifying the bytecode is valid, then preparing by allocating and initialising memory for class variables to default values. Finally, symbolic references are transformed into direct references to memory in the Method Area.

The last step is Initialisation, static variables will be initialised to their assigned starting values now that the memory has been allocated. 

### Runtime Data Area
#### Method Area
Class data, constants and static variables are stored in the method area. There is only one method area per JVM, and it is a shared resource. This method area is logically part of the Heap but implementations may treat this memory area differently and might not [[notes/Garbage Collection|Garbage Collect]] it. 
#### Heap Area
The heap memory is where all the Objects created by the application are stored. There is only one area per JVM and it is a shared resource. 

### Execution Engine
The Interpreter converts bytecode into machine code and executes it. The issue is that the interpreter will interpret all bytecode even if the same method is being called again. 

The Just In Time (JIT) compiler has a Profiler which monitors the code to identify which methods are frequently executed (hotspots).  The JVM identifies hotspots through keeping track of the number of times a method has been invoked. Once a threshold is exceeded, JIT compilation is triggered. The threshold for triggering JIT compilation can be configured and better performance can be achieved at the expense of higher compilation costs in terms of CPU and memory. 

Methods such as loops are common hotspot areas where optimisation is possible. When a hotspot is identified the JIT compiler will compile it to native machine code. Subsequent requests of the same method will then use the machine code which does not need to be interpreted which result in significant performance improvements.


#### Native Method Interface/Library
The Native Interface and Native method library are the libraries called to interact with the host machines OS. 
# References
- [JRE - IBM](https://www.ibm.com/topics/jre)
- [Java Virtual Machine - Medium](https://medium.com/@sanju.skm/java-virtual-machine-a1fc9e45d9d3)
- [Is the Java Virtual Machine the same as a VM](https://stackoverflow.com/questions/861422/is-the-java-virtual-machine-really-a-virtual-machine-in-the-same-sense-as-my-vmw)
- [Memory footprint of the JVM](https://spring.io/blog/2019/03/11/memory-footprint-of-the-jvm)
- [JIT Compiler - IBM](https://www.ibm.com/docs/en/sdk-java-technology/8?topic=reference-jit-compiler)