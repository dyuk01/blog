---
layout: post
title: Maximum Depth of Binary Tree
date: 2024-06-06
categories: leetcode python
---

## Problem
![alt text](/blog/public/img/MaxDepthBinaryTree.png)

## Approach
To make the approach simple, recursion can be used to find the maximum depth of a tree.

1. Find the depth of the left node
2. Find the depth of the right node
3. Find the maximum between the two, and add 1 to acquire the answer

## Code
```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def maxDepth(self, root):
        """
        :type root: TreeNode
        :rtype: int
        """
        if not root:
            return 0
        # Uses recursive to find the depth of left and right node, and finds the maximum. 1 is added to include the root node
        return 1 + max(self.maxDepth(root.left), self.maxDepth(root.right))
```

## Time Complexity
O(n)
> The algorithm visits node exactly once

## Space Complexity
O(h)
> Memory usage depends on the depth of the tree since recursion runs for depth amount

---