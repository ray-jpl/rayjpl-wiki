---
title: "Binary Tree - Level Order Traversal"
enableToc: true
tags:
- Binary Tree
- LeetCode
---

Level Order Traversal is essentially storing the nodes of each level/depth of the [[notes/Binary Tree]].

This can be performed iteratively using a Queue datastructure.
The general idea is to populate the queue with the nodes of the current level.
Now that the queue has all the nodes on that level, lets say N nodes, we just need to dequeue the next N nodes from the queue.
While we dequeue each node we can add its child nodes to the queue.
Once N nodes have been dequeued the queue will only be full of the nodes in the next level and then the cycle repeats. 
 

## Example
[Leetcode 102 - Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal/)
```java {title="Leetcode 102"}
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

class Solution {

    public List<List<Integer>> levelOrder(TreeNode root) {
        List<List<Integer>> result = new ArrayList();
        if (root == null) {
            return result;
        }
        Queue<TreeNode> treeQueue = new LinkedList<>();
        treeQueue.add(root);
        while (!treeQueue.isEmpty()) {
            int levelsize = treeQueue.size(); // Get size of Level

            List<Integer> levelList = new ArrayList(); // Stores all nodes on cur Level

            for (int i = 0; i < levelsize; i++) {
                TreeNode node = treeQueue.poll();
                if (node.left != null) treeQueue.add(node.left);
                if (node.right != null) treeQueue.add(node.right);
                levelList.add(node.val);
            }
            result.add(levelList);
        }

        return result;
    }

}
```

## Time Complexity
The algorithm involves traversing through all nodes in the tree using the Queue. 
Queue operations have O(1) time complexity. Therefore the while loop has a time complexity of O(N) as it involves adding and dequeuing a total of N nodes using the nested for-loop. 

## Space Complexity
The algorithm uses a queue data structure that store the nodes in the tree and therefore has a space complexity of O(N).


## References