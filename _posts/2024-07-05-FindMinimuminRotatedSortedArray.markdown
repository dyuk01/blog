---
layout: post
title: Find Minimum in Rotated Sorted Array
date: 2024-07-05
categories: leetcode python
---

## Problem
![alt text](/blog/public/img/FindMinimuminRotatedSortedArray.png)

## Approach
The input is in increasing order, but shifted n times. If we could find out how many times the original array was shifted(rotated), simply returning the first element of orginal array would be the answer

1. Find how many times the array was rotated
> Finding the minimum element within the array gives the index of shifted array. Since this element is the initial index in original array, simply finding the shifted index will give us the number of rotations

2. Return the smallest element

## Code
```python
class Solution(object):
    def findMin(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        l, r = 0, len(nums) - 1
        # Find the pivot
        while l < r:
            mid = (l + r) // 2
            if nums[mid] > nums[r]:
                l = mid + 1
            else:
                r = mid
        pivot = l

        # Return the first element of the array before rotation
        return nums[pivot]
```

## Time Complexity
O(log(n))
> Uses binary search for finding the pivot

## Space Complexity
O(1)
> Returns the smallest integer, which will always be one integer regardless of the input size

---