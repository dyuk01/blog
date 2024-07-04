---
layout: post
title: Find First and Last Position of Element in Sorted Array
date: 2024-07-04
categories: leetcode python
---

## Problem
![alt text](/blog/public/img/FindFirstandLastPositionofElementinSortedArray.png)

## Approach
 There are 3 cases: having no target, having one target, and having multiple target elements within the array. In order to solve an array with mutiple targets, we need to find leftmost index and rightmost index to solve this problem.

1. Initialize 1 loop to find the leftmost target index
2. Initialize 1 loop to find the rightmost target index  
3. Return leftmost and rightmost index as the answer

## Code
```python
class Solution(object):
    def searchRange(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        # Since l_res and r_res will be updated when target exists, we can intialize them as -1 for a case with no target within the array
        l_res = r_res = -1
        # No target found within the array
        if target not in nums:
            return [l_res, r_res]

        # Binary search to find the leftmost target's index
        l, r = 0, len(nums) - 1
        while l <= r:
            mid = (l + r) // 2
            if nums[mid] == target:
                l_res = mid
                r = mid - 1
                continue
            if nums[mid] < target:
                l = mid + 1
            else:
                r = mid - 1
        
        # Binary search to find the rightmost target's index
        l, r = 0, len(nums) - 1
        while l <= r:
            mid = (l + r) // 2
            if nums[mid] == target:
                r_res = mid
                l = mid + 1
                continue
            if nums[mid] < target:
                l = mid + 1
            else:
                r = mid - 1

        return [l_res, r_res]
```
## Time Complexity
O(log(n))
> Uses 2 binary search (1st to find the leftmost index, and 2nd to find the rightmost index), which makes the time complexity O(2log(n)) --> O(log(n))

## Space Complexity
O(1)
> Returns two integers, which does not increase as input size increases

---