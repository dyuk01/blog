---
layout: post
title: Rotate Image
date: 2024-07-27
categories: leetcode python
---
## Problem
![alt text](/blog/public/img/RotateImage.png)

## Approach
The easiest approach would be to initialize another 2d matrix and insert the values. However, this approach is forbidden by the question and occupies memory. So, we need to find a way to replace elements within the given matrix so that it looks rotated to the right. One way to achieve this is to

1. Reverse Matrix
> R

2. Transpose Matrix

## Code
```python
class Solution(object):
    def rotate(self, matrix):
        """
        :type matrix: List[List[int]]
        :rtype: None Do not return anything, modify matrix in-place instead.
        """
        n = len(matrix)
        # Reverse Matrix
        for i in range(n/2):
            for j in range(n):
                matrix[i][j],matrix[n-i-1][j] = matrix[n-i-1][j], matrix[i][j]

        # Transpose Matrix
        for i in range(n):
            for j in range(i):
                matrix[i][j], matrix[j][i] = matrix[j][i], matrix[i][j]

        return matrix
```

## Time Complexity
O()
> 

## Space Complexity
O()
> 

---