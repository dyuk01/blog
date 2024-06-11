---
layout: post
title: Minimum Absolute Difference in BST
date: 2024-06-10
categories: leetcode python
---

## Problem
![alt text](/blog/public/img/MinimumAbsoluteBST.png)

## Approach
The goal is to find the minimum value between the nodes. To achieve this, using recursion to traverse through the nodes will be sufficient.

## Code
```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    # Finds the minimum between the nodes by traversing through the nodes via recursion
    def findMin(self, node, l, h):
        # Reached the leaf node. Find the minimum
        if not node:
            return h - l
        left = self.findMin(node.left, l, node.val)
        right = self.findMin(node.right, node.val, h)
        return min(left, right)
    
    def getMinimumDifference(self, root):
        """
        :type root: TreeNode
        :rtype: int
        """
        return self.findMin(root, float('-inf'), float('inf'))
        
```

## Time Complexity
O(n)
> The algorithm traverses through the nodes in a tree. Thus having O(n)

## Space Complexity
O(n)
> On average, the space complexity required will be O(h). With it's extreme case of a tree having all left/right nodes, time complexity can result O(n)

---