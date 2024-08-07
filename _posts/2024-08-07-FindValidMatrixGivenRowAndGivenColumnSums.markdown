---
layout: post
title: Merge Nodes In Between Zeros
date: 2024-08-06
categories: leetcode python
---
## Problem
![alt text](/blog/public/img/MergeNodesInBetweenZeros.png)

## Approach


## Code
```python
class Solution(object):
    def restoreMatrix(self, rowSum, colSum):
        """
        :type rowSum: List[int]
        :type colSum: List[int]
        :rtype: List[List[int]]
        """
        res = [[0] * len(colSum) for i in range(len(rowSum))]
        row_sum = len(rowSum)
        col_sum = len(colSum)
        i = j = 0

        while i < row_sum and j < col_sum:
            res[i][j] = min(rowSum[i], colSum[j])
            if rowSum[i] == colSum[j]:
                i += 1
                j += 1
            elif rowSum[i] > colSum[j]:
                rowSum[i] -= colSum[j]
                j += 1
            else:
                colSum[j] -= rowSum[i]
                i += 1
            
        return res
```

## Time Complexity
O(m * n)
> 

## Space Complexity
O(m * n)
> Initializes a 2D matrix with length of given row and col

---