---
title: 0-1 Knapsack Problem
enableToc: true
tags:
  - BoundedKnapsack
  - DynamicProgramming
---
## 0/1 Knapsack Problem
The 0/1 Knapsack problem is often characterised by the problem having a capacity or target value that needs to be reached. We then have items that have "weights" which represent their value. A subset of items need to have a value that sum up to this target value. 

Other descriptions include: 
- Given a set of items, each with a weight and a value, determine which items to include in the collection so that the total weight is less than or equal to a given limit and the total value is as large as possible.
- **A resource allocation problem** where the decision-makers have to choose from a set of non-divisible projects or tasks under a fixed budget or time constraint.

The "0/1" means that we can either take 0 or take 1 for each item, this is also known as a bounded knapsack problem.

**Examples:**
- [[notes/Partition Equal Subset Sum|Partition Equal Subset Sum]]
- [Ones and Zeros](https://leetcode.com/problems/ones-and-zeroes/description/) (Similar to Partition Equal Subset Sum and similar optimisation available)
- [Number of Ways to Earn Points](https://leetcode.com/problems/number-of-ways-to-earn-points/description/)
