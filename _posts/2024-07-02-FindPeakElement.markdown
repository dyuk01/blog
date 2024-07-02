---
layout: post
title: Find Peak Element
date: 2024-07-02
categories: leetcode python
---

## Problem
![alt text](/blog/public/img/FindPeakElement.png)

## Approach
Another binary search problem since the question is asking for time complexity of log(n). Although it looks identical towards previous problems, it has possibility to have index out of bounds

1. Initialize left and right pointers for its both ends
2. Initialize pivot(mid) point on each iteration
3. Check for neighboring indexes to find peak element

## Code
```python
class Solution(object):
    def findPeakElement(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        l,r = 0, len(nums) - 1
        while l < r:
            mid = (l + r) // 2
            # Peak Element Found
            if nums[mid] > nums[mid - 1] and nums[mid] > nums[mid + 1]:
                return mid
            # Neighboring element on right is greater. Reduce lower half
            if nums[mid] <= nums[mid + 1]:
                l = mid + 1
            # Neighboring element on left is greater. Reduce upper half. (We cannot do mid - 1, since it is only iterating to right)
            else:
                r = mid - 1
        return l
```
## Time Complexity
O(log(n))
> Uses binary search to find the result from an array

## Space Complexity
O(1)
> Returns an int variable that does not increase with its input size

---