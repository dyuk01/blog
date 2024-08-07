---
layout: post
title: Merge Nodes In Between Zeros
date: 2024-08-06
categories: leetcode python
---
## Problem
![alt text](/blog/public/img/MergeNodesInBetweenZeros.png)

## Approach
The main approach is to find the minimum number between the current column and row. Then, move the grid to the greater number

1. Initailize 2D matrix with 0
2. Find the minimum number between column and row
3. Subtract the number from both side
4. Move the grid toward the number that is not 0
> Move toward greater number
5. Repeat until all conditions match

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
            # Finds the minimum number, and subtracts the minimum number from the greater number. Also, grid moves towards the greater number
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
> In worst case scenario, the algorithm will iterate through every grid in order to meet input's condition

## Space Complexity
O(m * n)
> Initializes a 2D matrix with length of given row and col

---