---
title: Dynamic Arrays
enableToc: true
tags:
---
# What is a Dynamic Array?
A dynamic array is an array that can grow in size. In traditional arrays the size of the array is fixed based on the capacity set during initialisation. When a traditional array is full you cannot increase its size, the only way to add more items is to initialise a new array that is larger in size and copy all the items from the old array into the new array. This is how most dynamic arrays are implemented in programming languages.

Dynamic Arrays are also known as Lists or vectors in other programming languages. 
## Growth Factor
When initialising a new array larger array, how much larger should we make it? The rate at which we grow the array is known as the growth factor. 

Each time the array gets full and a new insertion is required then the array needs to be resized. Resizing by a large growth factor can reduce average insertion runtime but increases the amount of memory required to be allocated. Having a low growth factor reduces the amount of wasted memory however frequent insertions could mean a higher average insertion runtime. 

The most common grow factors are 2 or 1.5. 

A growth factor like 1.5 has another advantage compared to 2. If you were using a first-fit memory allocator then when creating a new array it will try to allocate to the first block of memory that can fit it. 

To visualize, let "X" represent memory cells used by our array, and "O" represent memory cells that we can no longer use. A growth rate of 2X looks like so:

\[X\] -> \[OXX\] -> \[OOOXXXX\] -> \[OOOOOOOXXXXXXXX\]

Notice that for each resizing, the memory that is freed is less than the current memory that needs to be allocated. 

With a 1.5X growth multiplier, the memory usage looks like:
\[X\] -> \[OXX\] -> \[OOOXXX\] -> \[OOOOOOXXXX\] -> \[XXXXXX\]

In the second last resizing, notice that the number of empty cells is 6, therefore during the next resizing where we have 6 items we can allocate the new array to the memory we just freed.

The actual growth factor where this utilisation of earlier freed memory is only possible with a growth factor less than $\frac{(1+sqrt(5))}{2}\approx1.618$.

# References
- [Why is vector array doubled - Stack Overflow](https://stackoverflow.com/questions/1424826/why-is-vector-array-doubled/1426065#1426065)
- [Why does dynamic array always double by a factor of 2 - Stack Overflow](https://stackoverflow.com/a/72279477)
- [How does the capacity of stdvector grow automatically? - Stack Overflow](https://stackoverflow.com/questions/5232198/how-does-the-capacity-of-stdvector-grow-automatically-what-is-the-rate)
- [Vector Growth factor of 1.5 discussion](https://groups.google.com/g/comp.lang.c++.moderated/c/asH_VojWKJw)