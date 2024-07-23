---
layout: post
title: Swap Node In Pairs
date: 2024-07-23
categories: leetcode python
---
## Problem
![alt text](/blog/public/img/SwapNodeInPairs.png)

## Approach
The basic approach is similar to the "swapping numbers" method (utilizing variable `temp`). In this case, we apply this logic to the nodes of a linked list

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
        curr_node, curr_node.next = self, head
        while curr_node.next and curr_node.next.next:
            a = curr_node.next
            b = a.next
            curr_node.next, b.next, a.next = b, a, b.next
            curr_node = a
        return self.next
```
## Time Complexity
O(n)
> Iterates through the linked list exactly once

## Space Complexity
O(1)
> Uses constant amount of space for initializing node and temp that does not increase with the input size  

---