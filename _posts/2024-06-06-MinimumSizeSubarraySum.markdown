---
layout: post
title: Minimum Size Subarray Sum
date: 2024-06-06
categories: leetcode python
---

## Problem
![alt text](/blog/public/img/MinimumSizeSubarraySum.png)

## Approach
This problem needs to be solved with <a href="https://www.geeksforgeeks.org/window-sliding-technique/" target="_blank">window sliding</a> technique to have a time complexity of O(n).
## Code
```python
class Solution(object):
    def minSubArrayLen(self, target, nums):
        """
        :type target: int
        :type nums: List[int]
        :rtype: int
        """
        # In this algorithm, variable i will act as a rightmost index
        left = 0
        sum = 0
        # Maximum number that cannot be obtained from the array
        res = len(nums) + 1
        for i in range(len(nums)):
            sum += nums[i]
            while sum >= target:
                res = min(res, i - left + 1)
                sum -= nums[l]
                left += 1
        if res == len(nums) + 1:
            return 0
        return res
```

## Time Complexity
O(n)
> The loop iterates through the array once

## Space Complexity
O(1)
> Initializes 3 int variables that does not increase with the size of the array. Thus, O(1)

---