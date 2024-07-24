---
layout: post
title: Remove Nth Node From End of List
date: 2024-07-24
categories: leetcode python
---
## Problem
![alt text](/blog/public/img/RemoveNthNodeFromEndofList.png)

## Approach
The goal is to remove the Nth node from the end of a linked list. Since singly linked lists cannot be traversed backward, we need to first determine the position from the start by calculating the list's size and then find the target node

1. Calculate the size of the linked list
> Subtracting n from the size will give us the position from the start

2. Locate the nth index from the end

3. Handle edge cases
> When the nth index is first, middle, and last of the linked list

## Code
```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def removeNthFromEnd(self, head, n):
        """
        :type head: ListNode
        :type n: int
        :rtype: ListNode
        """
        # Determine the size of the list
        curr_node = head
        size = 0
        while curr_node:
            size += 1
            curr_node = curr_node.next

        # Out of Bound
        if size < n:
            return None

        curr_node = ListNode(0)
        curr_node.next = head
        rem_node = head

        # Iterate to the nth index
        for i in range(size - n):
            curr_node = curr_node.next
            rem_node = curr_node.next
        
        # First index
        if curr_node.next == head:
            head = head.next

        # Middle and Last index
        if rem_node and curr_node:
            curr_node.next = rem_node.next
            rem_node.next = None

        return head
```
## Time Complexity
O(n)
> The linked list is traversed twice (finding the size, and actually traversing for index adjustment), which results in O(2n). This simplies to O(n)

## Space Complexity
O(1)
> Uses constant space that does not increase with the input size

---