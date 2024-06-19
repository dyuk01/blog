---
layout: post
title: Merge Two Sorted Lists
date: 2024-06-19
categories: leetcode python
---

## Problem
![alt text](/blog/public/img/MergeTwoSortedLists.png)

## Approach
## Code
```python
class Solution(object):
    def mergeTwoLists(self, list1, list2):
        """
        :type list1: Optional[ListNode]
        :type list2: Optional[ListNode]
        :rtype: Optional[ListNode]
        """
        if not list1 or not list2:
            return list1 or list2
        if list1.val < list2.val:
            list1.next = self.mergeTwoLists(list1.next, list2)
            return list1
        else:
            list2.next = self.mergeTwoLists(list2.next, list1)
            return list2     
```

## Time Complexity
O(n)
> 

## Space Complexity
O(n)
> 

---