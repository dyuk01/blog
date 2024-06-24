---
layout: post
title: Search Insert Position
date: 2024-06-24
categories: leetcode python
---

## Problem
![alt text](/blog/public/img/SearchInsertPosition.png)

## Approach
Simple Binary search problem in order to find the target. One constraint is, when target is not present in the list, use has to return the predicted index position when inserted.

1. Perfrom the binary search 
> After finding the pivot point, reduce lower/upper half based on the comparison between pivot value and target

2. If target isn't present within the list, return the position of 'l' in order to predict the index value if target is inserted to the list

## Code
```python
class Solution(object):
    def searchInsert(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: int
        """
        l, r = 0, len(nums) - 1
        while l <= r:
            # Define middle(pivot)
            mid = (r + l) // 2
            # Target found
            if target == nums[mid]:
                return mid
            # Target greater than the lower half. Reduce the lower half
            elif target > nums[mid]:
                l = mid + 1
            # Target less than the upper half. Reduce the upper half
            else:
                r = mid - 1
        # Target is not present within the list. Return the predicted index value if inserted
        return l

        
```
## Time Complexity
O(logn)
> 

## Space Complexity
O(1)
> 

---