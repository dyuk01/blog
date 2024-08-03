---
layout: post
title: Dot Product of Two Sparse Vectors
date: 2024-08-03
categories: leetcode python
---
## Problem
![alt text](/blog/public/img/DotProductofTwoSparseVectors.png)

## Approach

## Code
```python
class SparseVector:
    def __init__(self, nums):
        """
        :type nums: List[int]
        """
        self.nums = nums


    # Return the dotProduct of two sparse vectors
    def dotProduct(self, vec):
        """
        :type vec: 'SparseVector'
        :rtype: int
        """
        res = 0
        for n, m in zip(self.nums, vec.nums):
            # If the number is not zero
            if n:
                res += n * m
        return res
        

# Your SparseVector object will be instantiated and called as such:
# v1 = SparseVector(nums1)
# v2 = SparseVector(nums2)
# ans = v1.dotProduct(v2)
```

## Time Complexity
O(n)
> Iterates through the array exactly once

## Space Complexity
O(1)
> Initializes and returns an int variable, which has fixed memory size

---