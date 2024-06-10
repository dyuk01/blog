---
layout: post
title: Minimum Absolute Difference in BST
date: 2024-06-10
categories: leetcode python
---

## Problem
![alt text](/blog/public/img/MinimumAbsoluteBST.png)

## Approach
The goal is to compare the order of 2 trees--p and q--and determine whether they are identical or not. Since we have to know if every node of a tree is equivalent to another, we need to traverse through each tree and compare them with another.

```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def isSameTree(self, p, q):
        """
        :type p: TreeNode
        :type q: TreeNode
        :rtype: bool
        """
        return str(p) == str(q)
```
The first approach was to turn the nodes into string and compare them. This can be an easy solution, but doesn't demonstrate any logic process. That is why I decided to use another way to solve the question despite its correctness.

## Code
```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def isSameTree(self, p, q):
        """
        :type p: TreeNode
        :type q: TreeNode
        :rtype: bool
        """
        # Reached the End
        if p is None and q is None:
            return True
        # Order is different from another
        if p is None or q is None:
            return False
        # Values are the same. Continue the recursion
        if p.val == q.val:
            return self.isSameTree(p.left, q.left) and self.isSameTree(p.right, q.right)
        return False
```
This algorithm uses recursion to traverse through the nodes. It first checks for the destination/failure scenarios, and keeps iterating through the nodes.

## Time Complexity
O(n)
> The algorithm only traverses through p and q nodes, which is O(n) + O(n) = O(2n). Resulting in O(n)

## Space Complexity
O(n)
> On average, the space complexity required will be O(h). With it's extreme case of a tree having all left/right nodes, time complexity can result O(n)

---