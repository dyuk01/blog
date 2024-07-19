---
layout: post
title: Merge Intervals
date: 2024-07-18
categories: leetcode python
---
## Problem
![alt text](/blog/public/img/MergeIntervals.png)

## Approach


## Code
```python
class Solution(object):
    def merge(self, intervals):
        """
        :type intervals: List[List[int]]
        :rtype: List[List[int]]
        """
        if not intervals:
            return []
        
        # Sort intervals based on the start time
        intervals = sorted(intervals, key=lambda x: x[0])
        
        res = []
        start, end = intervals[0]
        
        for i in range(1, len(intervals)):
            current_start, current_end = intervals[i]
            if current_start <= end:
                # Overlapping intervals, update the end if needed
                end = max(end, current_end)
            else:
                # Non-overlapping interval, add the previous interval and update
                res.append([start, end])
                start, end = current_start, current_end
        
        # Add the last interval
        res.append([start, end])
        
        return res
```
## Time Complexity
O(n)
> Iterates through the list until the last element

## Space Complexity
O(n)
> 

---