---
title: Target Sum
enableToc: true
tags:
  - DynamicProgramming
  - LeetCode
  - BoundedKnapsack
---
## Target Sum
[Leetcode 494 - Target Sum](https://leetcode.com/problems/target-sum/)

First we have to visualise the problem
For this array $A = [1,1,1,1,1]$ we apply either a subtract operation or addition operation on each value sequentially to reach some target number. 

Therefore the value of $A$ the sum after the first index is $-1$ or $1$. 
If we, simulate both operation and map out all the possible values for each index then we get the following.
$[1,-1],[2,0,-2],[3,1,-1,-3],[4,2,0,-2,-4],[5,3,1,-1,-3,-5]$

For index 4 one of the possible target values is 5.
The value for index 4, $A[4] = 1$, means that to reach 5 we have to add or subtract $1$. Therefore we would need to have a value of 6 or 4 as $6-1 = 4 + 1 = 5$. 

The possible values we can have at index 3 only contain $4$. If we repeat this process then we find out there is only one way to get $4$ by index 3.  

#### Defining the Subproblem 
We need to find the target sum, therefore we can describe our subproblem as: *"The number of expressions which evaluate to a target $T$  at index $k = EXP(k,T)$"*

Therefore for array $A$:
- $EXP(4,5) = 1$
- $EXP(4,3) = 3$
- $EXP(4,1) = 1$

I realised that for each index that the value of $EXP(T)$ would be different. It is possible to get $1$ and $-1$ at index 0 but not possible to get those values at index 1.  
If we consider the target 0 at index 1 there are two ways to get there. We can either subtract 1 from 1 to get 0 or add 1 to -1 to get 0. Therefore the number of expressions would be the number of ways to evaluate 1 plus the number of ways to evaluate -1. 

$$EXP(2,1) = EXP(1,0) + EXP(-1,0)$$


#### BFS + Memoization



**https://leetcode.com/problems/target-sum/description/ Write up BFS + MEMO SOLUTION**