---
title: "Binary Search Tree - In-Order Traversal"
enableToc: true
tags:
- Binary Search Tree
- Binary Tree
- LeetCode
---

Inorder search for a [[notes/Binary Search Tree]] searches nodes from lowest to highest.

As Binary search trees are ordered in a way that all nodes in the left subtree contain a lower value than the current node. We can use this property and traverse to the leftmost node in the tree which will be the beginning of our search.

Given that the current node is the smallest then we must traverse through its right subtree in order to find the next larger nodes. Once the right subtree is exhausted we go up a level/depth and repeat.


## Example
[LeetCode 94 - Binary Tree Inorder Traversal] 
```java {title=Leetcode 94}
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }

 */

// The iterative solution can utilise a stack to keep track of the parent nodes
class Solution {
    public List<Integer> inorderTraversal(TreeNode root) {
        List<Integer> list = new ArrayList<Integer>();
        if(root == null) return list;
  
        Stack<TreeNode> stack = new Stack<>();

        while(root != null || !stack.empty()){
            while(root != null){
                // Go to the leftmost node possible
                stack.push(root);
                root = root.left;
            }
            // Once leftmost is reached traverse right subtree and then repeat
            root = stack.pop();
            list.add(root.val);
            root = root.right;
        }
        return list;
    }
}

// Recursive solution follows same logic
// Go as far left as you can then add the node,
// Then traverse right subtree in a similar manner
class Solution {
    List<Integer> list = new ArrayList<Integer>();
    public List<Integer> inorderTraversal(TreeNode root) {
        traverse(root);
        return list;
    }

    public void traverse(TreeNode root) {
        if (root != null) {
            traverse(root.left);
            list.add(root.val);
            traverse(root.right);
        }
    }
        
}
```

## Time Complexity
Both solutions have to iterate over every node in the tree and therefore there it has O(N) worst case time complexity. 

## Space Complexity
For the iterative solution the Stack is the only data structure and it has a space complexity of O(H) where H is the height of the tree. In the worst case has an O(N) space complexity where the entire tree is just leftnodes. 

For the recursive case if you do not count the call stack then it has a space complexity of O(1), otherwise the space complexity is the same as the iterative solution. 

## References