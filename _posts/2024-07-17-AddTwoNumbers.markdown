---
layout: post
title: Add Two Numbers 
date: 2024-07-17
categories: leetcode python
---

## Problem
![alt text](/blog/public/img/AddTwoNumbers.png)

## Approach


## Code
```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def addTwoNumbers(self, l1, l2):
        """
        :type l1: ListNode
        :type l2: ListNode
        :rtype: ListNode
        """
        # Initialize the root as the root node
        root = res = ListNode(0)
        carry = 0
        # While there are elements in l1 or l2, and rounding process is incomplete
        while l1 or l2 or carry:
            # Rounding up(0 or 1) from a previous process
            sum = carry
            if l1:
                sum += l1.val
                l1 = l1.next
            if l2:
                sum += l2.val
                l2 = l2.next
            # Carry becomes roundUp, val becomes remainder
            carry, val = divmod(sum, 10)
            res.next = ListNode(val)
            res = res.next
        return root.next
```
## Time Complexity
O(n)
> Iterates through both list nodes exactly once

## Space Complexity
O(n)
> 

---