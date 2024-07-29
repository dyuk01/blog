---
layout: post
title: Number of Islands 
date: 2024-07-29
categories: leetcode python
---
## Problem
![alt text](/blog/public/img/NumberOfIslands.png)

## Approach


## Code
```python
class Solution(object):
    def numIslands(self, grid):
        """
        :type grid: List[List[str]]
        :rtype: int
        """
        # No grid available = No Islands
        if not grid:
            return 0
        
        res = 0
        def dfs(grid, col, row):
            '''
            Cannot run dfs on following conditions
                1. Coordinates are out of bounds
                    - Negative numbers
                    - Exceeds grid bounds
                2. Targetted coordinate is water
                    - Not '1'
            '''
            if col < 0 or row < 0 or col >= len(grid) or row >= len(grid[0]) or grid[col][row] != '1':
                return
            # Sets special character (not integer) to identify visited land
            grid[col][row] = '@'
            # Explores new coordinates (east, west, north, south)
            dfs(grid, col + 1, row)
            dfs(grid, col - 1, row)
            dfs(grid, col, row + 1)
            dfs(grid, col, row - 1)
        
        # Explores every coordinate on grid and return the number of islands
        for i in range(len(grid)):
            for j in range(len(grid[0])):
                if grid[i][j] == '1':
                    dfs(grid, i, j)
                    res += 1
        
        return res
```

## Time Complexity
O(n)
> Initializes a list, iterates the string twice(from left to right, and right to left), and joins the string all together which results in O(4n). This simplifies to O(n)

## Space Complexity
O(n)
> Converts string elements into a list

---