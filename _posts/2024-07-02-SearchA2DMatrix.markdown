---
layout: post
title: Search A 2D Matrix
date: 2024-07-02
categories: leetcode python
---

## Problem
![alt text](/blog/public/img/SearchA2DMatrix.png)

## Approach
This problem is a simple binary search with the aspect of 2D array.

1. Initialize left and right pointers for both ends
2. Find the middle(pivot) point, and set the index to the pivot array
3. If the target is not found within the pivot array, we can initialize matrix[mid][0] as our comparison since we know that the number is not present within the area. Thus, making any number within the pivot array valid for comparison
4. Loop through the algorithm until target is found / not found

## Code
```python
class Solution(object):
    def searchMatrix(self, matrix, target):
        """
        :type matrix: List[List[int]]
        :type target: int
        :rtype: bool
        """
        l,r = 0, len(matrix) - 1
        while l <= r:
            mid = (l + r) // 2
            # Found target within the pivot array
            if target in matrix[mid]:
                return True
            # Target less than pivot array. Reduce upper half
            elif target < matrix[mid][0]:
                r = mid - 1
            # Target greater than pivot array. Reduce lower half
            else:
                l = mid + 1
        return False
```
## Time Complexity
O(log(n*m))
> At worst scenario, the algorithm iterates through every row in order to find the target, which results in O(m*n). However, this algorithm uses binary search, which reduces the time complexity to O(log(m*n))

## Space Complexity
O(1)
> Returns a boolean statement(True/False) that is regardless of the input size

---