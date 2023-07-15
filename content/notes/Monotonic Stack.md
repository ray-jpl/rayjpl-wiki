---
title: "Monotonic Stack"
enableToc: true
tags:
- Stack
- LeetCode
---
## Monotonic Stack
A Monotonic stack is a stack where the elements are increasing or decreasing. To keep the order of elements we pop smaller/larger elements from the stack before pushing the new element. 

## Example
[LeetCode 84 - Largest Rectangle In Histogram](https://leetcode.com/problems/largest-rectangle-in-histogram/description/)
```java {title="Largest Rectangle In Histogram"}
class Solution {
    public int largestRectangleArea(int[] heights) {
        int maxArea = 0;
        Stack<int[]> stack = new Stack<>();

        for (int i = 0; i < heights.length; i++) {
            int start = i;
            while (!stack.empty() && stack.peek()[1] > heights[i]) {
                int[] prev = stack.pop();
                int index = prev[0];
                int height = prev[1];
                maxArea = Math.max(maxArea, height * (i-index));
                start = index;
            }
            stack.push(new int[]{start, heights[i]});
        }

        // May still be entries in the stack
        // These entries extend all the way to the end of the histogram from their current position

        while (!stack.empty()) {
            int[] prev = stack.pop();
            int index = prev[0];
            int height = prev[1];
            maxArea = Math.max(maxArea, height * (heights.length - index));
        }
        return maxArea;
    }
}
```

This solution is derived from [NeetCode's video](https://www.youtube.com/watch?v=zx5Sw9130L0) but I wanted to understand the code and concept a bit more.

When traversing the array of heights from left to right there are three cases to consider. 

Case 1. The previous height is larger than the current one. 
Case 2. The previous height is smaller than the current one.
Case 3. The previous height is the same as the current one.


