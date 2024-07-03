---
layout: post
title: Search In Rotated Sorted Array
date: 2024-07-03
categories: leetcode python
---

## Problem
![alt text](/blog/public/img/SearchInRotatedSortedArray.png)

## Approach
Blindly using binary search will not work since its contents are no longer sorted when rotated. To tackle this problem, we need to first find the pivot point, then use binary search according to the pivot point found:

1. Find the Pivot
> Use binary search to find the pivot where the array is rotated  
Initialize two pointers, l and r, at the start and end of the array  
Check the middle element. If it is greater than the next element, then the middle element is the pivot  
Adjust the left or right pointers based on the middle element's comparison with the first element

2. Binary Search on the Correct Subarray
> Once the pivot is identified, determine which subarray (left or right of the pivot) contains the target value and perform a binary search on that subarray

## Code
```python
class Solution(object):
    def search(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: int
        """
        # Target not present within the array
        if not nums:
            return -1
        
        # Finds the index of pivot before rotation
        def find_pivot(nums):
            l, r = 0, len(nums) - 1
            while l < r:
                mid = (l + r) // 2
                if nums[mid] > nums[r]:
                    l = mid + 1
                else:
                    r = mid
            return l
        
        # Finds the index of target number
        pivot = find_pivot(nums)
        l, r = 0, len(nums) - 1
        while l <= r:
            mid = (l + r) // 2
            real_mid = (mid + pivot) % len(nums)
            
            if nums[real_mid] == target:
                return real_mid
            elif nums[real_mid] < target:
                l = mid + 1
            else:
                r = mid - 1
        
        return -1
```
## Time Complexity
O(log(n))
> Uses 2 binary search (1st to find the pivot, and 2nd to find the target), which makes the time complexity O(2log(n)) --> O(log(n))

## Space Complexity
O(1)
> Returns a index number of the target, which is constant

---