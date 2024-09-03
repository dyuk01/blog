---
layout: post
title: Swap Node In Pairs
date: 2024-07-23
categories: leetcode python
---
## Problem
![alt text](/blog/public/img/SwapNodeInPairs.png)

## Approach
The basic approach is similar to the "swapping numbers" method (utilizing variable `temp`). In this case, we apply this logic to the nodes of a linked list. Since we cannot start from the initial and have initial.next due to None type, we must initialize from the previous node

## Code
```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def swapPairs(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        # Sets previous and its' link
        prev, prev.next = self, head
        while prev.next and prev.next.next:
            a = prev.next
            b = a.next
            prev.next, b.next, a.next = b, a, b.next 
            prev = a
        return self.next
```

## Time Complexity
O(n)
> Iterates through the linked list exactly once

## Space Complexity
O(1)
> Uses constant amount of space for initializing node and temp that does not increase with the input size  

---