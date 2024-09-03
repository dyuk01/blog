---
layout: post
title: Buildings With An Ocean View
date: 2024-08-03
categories: leetcode python
---
## Problem
![alt text](/blog/public/img/BuildingsWithAnOceanView.png)

## Approach

## Code
```python
class Solution(object):
    def findBuildings(self, heights):
        """
        :type heights: List[int]
        :rtype: List[int]
        """
        res = []
        max = -1
        # Since ocean is on the right, we iterate from the right to left to find out ocean view building
        for i in range(len(heights) - 1, -1, -1):
            # Taller building found
            if heights[i] > max:
                res.append(i)
                max = heights[i]
        # Since list has to be sorted, sort the list
        res.sort()
        return res
```

## Time Complexity
O(nlogn)
> Iterates through the array exactly once, but sorts the array which is O(nlogn)

## Space Complexity
O(n)
> 

---