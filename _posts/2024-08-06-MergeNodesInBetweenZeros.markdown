---
layout: post
title: Merge Nodes In Between Zeros
date: 2024-08-06
categories: leetcode python
---
## Problem
![alt text](/blog/public/img/MergeNodesInBetweenZeros.png)

## Approach
1. Iterate through the list
2. While iteration, make sum of the values between 0
3. Link the sum with the current node, and the next node as the number after 0

## Code
```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def mergeNodes(self, head):
        """
        :type head: Optional[ListNode]
        :rtype: Optional[ListNode]
        """
        # Dummy node
        modify = head.next
        next_sum = modify
        
        while next_sum:
            sum = 0
            # Add any none-zero nodes' value into sum
            while next_sum.val != 0:
                sum += next_sum.val
                next_sum = next_sum.next
            # Changes the current node to sum, and links the next node to the node after 0
            modify.val = sum
            next_sum = next_sum.next
            modify.next = next_sum
            modify = modify.next
        return head.next
```

## Time Complexity
O(n)
> Iterates through the linked list exactly once

## Space Complexity
O(1)
> Initializes fixed amount of nodes that does not increase with the input size

---