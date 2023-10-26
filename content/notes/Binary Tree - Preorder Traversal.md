---
title: Binary Tree - Preorder Traversal
enableToc: true
tags:
  - BST
  - Tree
---
## Preorder Traversal
Preorder traversal searches the root node then traverses the left subtree, then the right subtree.

This is commonly used to create a copy of a tree.

Here is an example of a preorder traversal
The result should be = \[1,4,3,5,2]
![[files/Pasted image 20231026222635.png]]

[Leetcode 144 - Preorder Traversal](https://leetcode.com/problems/binary-tree-preorder-traversal/description/)
```java {title=Leetcode 144}
// Iterative Solution
class Solution {
    public List<Integer> preorderTraversal(TreeNode root) {
        List<Integer> result = new ArrayList<>();
        if (root == null) {
            return result;
        }
        Stack<TreeNode> stack = new Stack<>();
        stack.push(root);
        while(!stack.isEmpty()) {
            TreeNode node = stack.pop();
            result.add(node.val);
            if (node.right != null) {
                stack.push(node.right);
            }
            if (node.left != null) {
                stack.push(node.left);
            }
        }
        return result;
    }
}

// Recursive Solution
class Solution {
    List<Integer> result = new ArrayList<>();
    public List<Integer> preorderTraversal(TreeNode root) {
        if (root == null) {
            return result;
        }
        result.add(root.val);
        preorderTraversal(root.left);
        preorderTraversal(root.right);
        return result;
    }
}
```