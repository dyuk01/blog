---
layout: post
title: Kth Largest Element In an Array
date: 2024-06-21
categories: leetcode python
---

## Problem
![alt text](/blog/public/img/KthLargestElementInAnArray.png)

## Approach
The goal is to find the kth maximum array from the list. Without using any kind of sorting, we can solve this problem with heap which naturally stores minimum value at the top(min-heap).

1. Initialize heap
2. Store the integers in the list as negative integers
> Because heaps in python are initialized as min-heap in default, we have to turn the input integers into negative in order to get the maximum integer at the top
3. Pop the heap k times in order to get kth largest element
> Note that popped element has to be turned negative also, in order to have them into a positive integer

## Code
```python
import heapq
class Solution(object):
    def findKthLargest(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: int
        """
        h = []
        # Stores elements in max-heap
        for i in range(len(nums)):
            heapq.heappush(h, -nums[i])
        # Pops the heap k times
        for i in range(k):
            res = -heapq.heappop(h)
        # Return the k-times popped element
        return res
```

## Time Complexity
O(nlogn)
> heapq.heappop() and heappush() have time complexity of O(logn), and the for loop runs n times. Resulting in O(nlogn)

## Space Complexity
O(n)
> Initializes heap that stores entire input array

---