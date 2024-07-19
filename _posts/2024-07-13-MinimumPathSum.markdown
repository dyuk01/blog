---
layout: post
title: MinimumPathSum
date: 2024-07-13
categories: leetcode python
---

## Problem
![alt text](/blog/public/img/MinimumPathSum.png)

## Approach


## Code
```python
class Solution(object):
    def minPathSum(self, grid):
        m = len(grid)
        n = len(grid[0])
        for i in range(1, n):
            grid[0][i] += grid[0][i-1]
        for i in range(1, m):
            grid[i][0] += grid[i-1][0]
        for i in range(1, m):
            for j in range(1, n):
                grid[i][j] += min(grid[i-1][j], grid[i][j-1])
        return grid[-1][-1]
```
## Time Complexity
O(n<sup>2</sup>)
> 

## Space Complexity
O(n)
> 

---