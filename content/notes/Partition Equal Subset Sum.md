---
title: Partition Equal Subset Sum
enableToc: true
tags:
  - DynamicProgramming
  - LeetCode
  - BoundedKnapsack
---
## Partition Equal Subset Sum
[Leetcode 416 - Partition Equal Subset Sum](https://leetcode.com/problems/partition-equal-subset-sum/description/)
#### Classifying the problem
The problem here looks like a [[notes/0-1 Knapsack Problem|0-1 Knapsack Problem]].
We need to reach some target, in this case the target is half of the total sum of all elements in the array. 
Our items here are the numbers in the array that are used to calculate the total sum. We need to find a subset of these numbers that add to the target.

If one subset is equal to the target that means the remaining elements must add up to the same target. 
#### States
*Index:* For each index we can either choose to use that number in our subset or ignore it.  The index tells us what values we have considered, what values we haven't considered, and what value we are currently considering. As a general rule, index is a required state in nearly all dynamic programming problems

*Current Sum:*  Current Sum gives us the sum of all the values we have processed so far. Our answer revolves around the Current Sum being equal to Target

#### Define the Subproblem
Consider the this example $A = [2,3,4,5]$.
The elements add up to 14 therefore $target = 7$

We can describe our subproblem as: *If the target sum T is reachable at  index K = $isReachable(K, T)$*

For array A.
- $isReachable(0, 1) = False$
- $isReachable(0, 2) = True$
- $isReachable(1, 2) = True$
- $isReachable(1, 3) = True$

#### Define the relationship between subproblems
The cases that interest me are 
-  $isReachable(1, 2) = True$
- $isReachable(1, 5) = True$


For the first subproblem, $isReachable(1,2)$, the answer is true because although $A[1] = 3$ is larger than the target we need to check if the target has been reached by the previous index. Or we can phrase that as  "if the subproblem $isReachable(0,2) = True$"".
$$isReachable(1, 2) = isReachable(0,2)$$

For the second subproblem, $isReachable(1, 5) = True$.
Based on the previous subproblem we need to check if the subproblem has already been reached before, check if 5 has been reached before by solving the subproblem $isReachable(0,5)$.
Otherwise to reach $target = 5$, we need to check if a 2 exists already this way we can add $A[1] = 3$  to make 5. 
$$isReachable(1, 5) = isReachable(0,5)\;\;\; \text{OR} \;\;\; isReachable(0,2)$$
We can only check for 2 since our current value is less than the target, $T-A[i] >= 0$, otherwise we cant check for the complementary number.


We can generalise this relationship to 
$$isReachable(i,T) = isReachable(i-1, T) \;\;\; OR \;\;\; \{isReachable(i-1, T-A[i])\; | \; T-A[i] \geq 0\}$$
#### Implementation
Lets create a 2D array of our States. 
Let the horizontal axis represent our current sum and let the vertical axis represent our items.
Notice that the array has a zero value for both the target value and the set. This extra zero column and row will assist in the backtracking needed.

| ~ | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
| - | - | - | - | - | - | - | - | - |
| 0 | T | F | F | F | F | F | F | F |
| 2 | T | - | - | - | - | - | - | - |
| 3 | T | - | - | - | - | - | - | - |
| 4| T | - | - | - | - | - | - | - |
| 5 | T | - | - | - | - | - | - | - |

We can interpret the table like so. Can we use the value on the left to equal the target sum at the top of the table?
For the first row we can see that 0 value can be used to reach a target sum of 0, subsequent values cannot be made with 0.

---

| ~ | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
| - | - | - | - | - | - | - | - | - |
| **0** | T | F | F | F | F | F | F | F |
| **2** | T | F | T | F | F | F | F | F |
| **3** | T | - | - | - | - | - | - | - |
| **4**| T | - | - | - | - | - | - | - |
| **5** | T | - | - | - | - | - | - | - |

Now for the first value "2". 
- We can make the current sum 0 by not using 2.
- Cannot make the current sum 1 as 2 > 1. 
- We can make the current sum 2 as 2 = 2.
- The subsequent sums cannot be made with 2. 

---

| ~ | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
| - | - | - | - | - | - | - | - | - |
| **0** | T | F | F | F | F | F | F | F |
| **2** | T | F | T | F | F | F | F | F |
| **3** | T | F | T | T | F | T | F | F |
| **4**| T | - | - | - | - | - | - | - |
| **5** | T | - | - | - | - | - | - | - |

Now for the value "3". 
- We can make the current sum 0 still. 
- Cannot make current sum 1 as 3 > 1;
- We can make the current sum 2 as we can include the previous item "2" and exclude the current item 3 to make the set $\{2\}$
- We can make the current sum 3 as 3 = 3.
- We cannot make the current sum 4. To make the current sum =  4, the previous item should have a set with a total sum of 1 so that we can make $1+ 3=4$. Based on our table there is no set of numbers at the item with value "2" to make 1. 
- We can make the current sum 5. The previous row has a valid set for a current sum = 2, and $2+3=5$, this set would be $\{2,3\}$
---

| ~ | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
| - | - | - | - | - | - | - | - | - |
| **0** | T | F | F | F | F | F | F | F |
| **2** | T | F | T | F | F | F | F | F |
| **3** | T | F | T | T | F | T | F | F |
| **4**| T | F | T | T | T | T | T | T |
| **5** | T | - | - | - | - | - | - | - |

Now for the item with value "4"
- We can make a current sum 6. The previous row has a valid set for a current sum for 2. By adding 4 we reach 6, this set would be $\{2,4\}$
- We can also make a current sum of 7. The previous row has a valid set for a current sum 3, the set would be $\{3.4\}$
---

| ~ | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
| - | - | - | - | - | - | - | - | - |
| **0** | T | F | F | F | F | F | F | F |
| **2** | T | F | T | F | F | F | F | F |
| **3** | T | F | T | T | F | T | F | F |
| **4**| T | F | T | T | T | T | T | T |
| **5** | T | F | T | T | T | T | T | T |

We repeat this same process for the item with value "5".

```java
class Solution {
    public boolean canPartition(int[] nums) {
        int target = 0;
        for (int num: nums) {
            target += num;
        }
        if (target % 2 == 1) {
            return false;
        }
        target /= 2;

        // Init DP array
        boolean[][] dp = new boolean[nums.length + 1][target + 1];
        // Init first row to false
        for (int i = 1; i < target + 1; i++) {
            dp[0][i] = false;
        }

        // Init first col to true
        for (int j = 0; j < nums.length + 1; j++) {
            dp[j][0] = true;
        }

        // Start at index [1][1] as first and 2nd columns are base cases
        for (int i = 1; i < nums.length + 1; i++) {
            for (int curSum = 1; curSum < target + 1; curSum++) {
                // Check if already reached
                dp[i][curSum] = dp[i-1][curSum];
                if (curSum >= nums[i-1]) {
                    // Since i represents the size of the dp array with the 0 value
                    // we need to decrement by 1 to get the correct index for 
                    // nums[i-1]
                    dp[i][curSum] = dp[i-1][curSum] || dp[i-1][curSum-nums[i-1]];
                }
            }
        }
        return dp[nums.length][target];
    }
}
```

## Extension - Optimisation

From the graphical representation we can see that there is a lot of repeated reading of values. If the Current Sum is true then it stays true for each subsequent item. Therefore we should be able to condense this into one array.

Lets step through this again visually

| ~ | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
| - | - | - | - | - | - | - | - | - |
| **0** | T | F | F | F | F | F | F | F |

This is the array when its initialised.
Lets reuse the code and refactor it to use this single array. If we just remove all instances of the number index we get this. At first glance this should look it like it would work but it does not.
```java
for (int i = 1; i < nums.length + 1; i++) {
	for (int curSum = 1; curSum < target + 1; curSum++) {
		if (curSum >= nums[i-1]) {
			dp[curSum] = dp[curSum] || dp[curSum-nums[i-1]];
		}
	}
}
```


If we step through with $nums[i] = 2$, once we get to $\text{curSum}=4$ we realise that 

$$\begin{eqnarray}
dp[\text{curSum}-nums[i-1]] &=& dp[4-2]\\ 
&=& dp[2]\\
&=& True
\end{eqnarray}$$
Which means $dp[4] = True$ which should not be correct.

| ~ | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
| - | - | - | - | - | - | - | - | - |
| **2** | T | F | T | F | **T**\* | - | - | - |

This is because we need to read the values on the left to compute the Current Sum, values that we just wrote to. To avoid this issue we can simply just iterate from right to left.


```java
class Solution {
    public boolean canPartition(int[] nums) {
        int target = 0;
        for (int num: nums) {
            target += num;
        }

        if (target % 2 == 1) {
            return false;
        }

        target /= 2;

        // Init DP array
        boolean[] dp = new boolean[target+1];
        dp[0] = true;

        for (int i = 0; i < nums.length; i++) {
            // NOTE: The curSum loop iterates from target -> 0 instead
            for (int curSum = target; curSum >= 0; curSum--) {
                if (curSum >= nums[i]) {
                    dp[curSum] = dp[curSum] || dp[curSum - nums[i]];
                }
            }
        }
        return dp[target];
    }
}
```