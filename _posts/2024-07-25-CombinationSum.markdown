---
layout: post
title: Combination Sum
date: 2024-07-25
categories: leetcode python
---
## Problem
![alt text](/blog/public/img/CombinationSum.png)

## Approach
Because we have to find all combinations to form a target number, we will use dfs to find all possible combinations to form the target number

## Code
```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def removeNthFromEnd(self, head, n):
class Solution(object):
    def combinationSum(self, candidates, target):
        """
        :type candidates: List[int]
        :type target: int
        :rtype: List[List[int]]
        """
        res = []
        def dfs(candidates, target, combination, res):
            # Invalid Number
            if target < 0:
                return
            # Target number found
            if target == 0:
                res.append(combination)
                return
            # Since the combination is ordered, we can safely iterate from the smallest number to the biggest number
            for i in range(len(candidates)):
                dfs(candidates[i:], target - candidates[i], combination + [candidates[i]], res)

        dfs(candidates, target, [], res)
        return res
```
## Time Complexity
O(n)
> 

## Space Complexity
O(1)
> 

---