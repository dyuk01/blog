---
layout: post
title: Minimum Size Subarray Sum
date: 2024-06-06
categories: leetcode python
---

## Problem
![alt text](/blog/public/img/MinimumSizeSubarraySum.png)

## Approach


## Code
```python
class Solution(object):
    def minSubArrayLen(self, target, nums):
        """
        :type target: int
        :type nums: List[int]
        :rtype: int
        """
        l = 0
        sum = 0
        res = len(nums) + 1
        for i in range(len(nums)):
            sum += nums[i]
            while sum >= target:
                res = min(res, i - l + 1)
                sum -= nums[l]
                l += 1
        if res == len(nums) + 1:
            return 0
        return res
```

## Time Complexity
O(n)
> 

## Space Complexity
O(h)
> 

---