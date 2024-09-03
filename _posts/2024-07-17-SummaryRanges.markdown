---
layout: post
title: Summary Ranges 
date: 2024-07-17
categories: leetcode python
---
## Problem
![alt text](/blog/public/img/SummaryRanges.png)

## Approach
The object is to find the consecutive numbers in a list, and express them into an interval using arrow("->") notation.

1. Check out of bounds
> Since next element will be accessed to compare consecutiveness, make sure to check for bounds

2. 

## Code
```python
class Solution(object):
    def summaryRanges(self, nums):
        """
        :type nums: List[int]
        :rtype: List[str]
        """
        res = []     
        i = 0 
        while i < len(nums): 
            # Initializes starting point
            start = nums[i]  
            # Check Out of bounds & consecutive numbers
            while i + 1 < len(nums) and nums[i] + 1 == nums[i + 1]: 
                i += 1 
            
            # Interval ended
            if start != nums[i]: 
                # There are more than 1 numbers in an interval
                res.append(str(start) + "->" + str(nums[i]))
            else: 
                # Only one number exists for an interval
                res.append(str(nums[i]))
            
            i += 1

        return res
```

## Time Complexity
O(n)
> Iterates through the list until the last element

## Space Complexity
O(n)
> 

---