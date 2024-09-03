---
layout: post
title: Linked List Cycle
date: 2024-06-13
categories: leetcode python
---

## Problem
![alt text](/blog/public/img/LinkedListCycle.png)

## Approach
The goal is to find the existence of a cycle within a linked list. In order to do this, I will be using Floyd's Cycle Finding Algorithm.

## Code
```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def hasCycle(self, head):
        """
        :type head: ListNode
        :rtype: bool
        """
        try :
            curr_node = head
            next_node = curr_node.next
            # Next_node eventually catches up to curr_node if there is a cycle
            while curr_node != next_node:
                curr_node = curr_node.next
                next_node = next_node.next.next
            return True
        except:
            return False        
```

## Time Complexity
O(n)
> Only iterates through the list once

## Space Complexity
O(n)
> Initializes 'node' variables, which is the length of the given linked list

---