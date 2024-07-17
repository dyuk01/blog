---
layout: post
title: Summary Ranges 
date: 2024-07-17
categories: leetcode python
---

## Problem
![alt text](/blog/public/img/SummaryRanges.png)

## Approach


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
            start = nums[i]  
            while i + 1 < len(nums) and nums[i] + 1 == nums[i + 1]: 
                i += 1 
            
            if start != nums[i]: 
                res.append(str(start) + "->" + str(nums[i]))
            else: 
                res.append(str(nums[i]))
            
            i += 1

        return res
```
## Time Complexity
O()
> 

## Space Complexity
O()
> 

---