---
title: Binary Tree - Postorder Traversal
enableToc: true
tags:
  - BST
  - Tree
---
## Postorder Traversal

Postorder traversal involves traversing the left subtree, then the right subtree then the root node. 

It is commonly used to delete binary trees as you search from bottom-up. 
The recursive solution for postorder traversal is similar to [[notes/Binary Tree - Preorder Traversal|Preorder Traversal]] so take care.

Note: The top solutions in the LeetCode discussion section do not actually visit these nodes in a  postorder manner but rather just output the answer in postorder. 
[LeetCode 145 - Postorder Traversal](https://leetcode.com/problems/binary-tree-postorder-traversal/description/)
```java {title=LeetCode 145}
// Iterative Solution
class Solution {
    public List<Integer> postorderTraversal(TreeNode root) {
        List<Integer> result = new ArrayList<>();
        
        Stack<TreeNode> stack = new Stack();
        while(!stack.isEmpty() || root != null) {
            if (root != null) {
                stack.add(root);
                root = root.left; //Traverse left as far as you can
            } else {
                TreeNode temp = stack.peek().right; // Check if right subtree exists
                if(temp == null) {
                    temp = stack.pop(); 
                    result.add(temp.val);
                    // If current node is the right subtree of a parent node then pop
                    while(!stack.isEmpty() && temp == stack.peek().right) {
                        temp = stack.pop();
                        result.add(temp.val);
                    }
                } else {
                    root = temp; // Right subtree exists
                }
            }
        }
        return result;
    }
}

// Recursive Solution
class Solution {
    public List<Integer> postorderTraversal(TreeNode root) {
        List<Integer> result = new ArrayList<>(); 
        postorderTraversalRecursive(root, result);
        return result;
    }
  
    public void postorderTraverse(TreeNode node, List<Integer> result) {
        if (node == null) {
            return;
        }
        postorderTraverse(node.left, result);
        postorderTraverse(node.right, result);
        // Visit the root node
        result.add(node.val);
    }
}
```