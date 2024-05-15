---
layout: post
title: Merge Sorted Array
date: 2024-05-14 15:56:00 +0900
categories: leetcode python
---
## Problem
![alt text](/blog/public/img/MergeSortedArray.png)

## Approach
Since there has to be an array with size of m + n, appending nums1 by the size of n would be sufficient enough.  
Then, sort the array with sort function to acquire the solution.

## Code
```python
class Solution(object):
    def merge(self, nums1, m, nums2, n):
        for i in range(n):
            nums1[i + m] = nums2[i]
        nums1.sort()
```
## Time Complexity
Because this code uses sort function, the time complexity would be O(n log(n)).  
However, since the code iterates through array size of m and n, the overall time complexity would be O((m+n)log(m+n)).

## Space Complexity
O(1) since this code does not occupy any space.