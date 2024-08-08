---
layout: post
title: Spiral Matrix III
date: 2024-08-09
categories: leetcode python
---
## Problem
![alt text](/blog/public/img/SpiralMatrix3.png)

## Approach
The goal is to find the pattern of the spiral.

1. Spiral spins clock-wise
2. Length of spiral increments by 1 every 2 turn
3. Direction is always in order : East, South, West, North
4. Spiral needs to be happening even if the spiral goes out of bound

With these patterns in mind, we only need to implement the steps into code
## Code
```python
class Solution(object):
    def spiralMatrixIII(self, rows, cols, rStart, cStart):
        """
        :type rows: int
        :type cols: int
        :type rStart: int
        :type cStart: int
        :rtype: List[List[int]]
        """
        # East, South, West, North
        dir = [[0,1], [1,0], [0,-1], [-1,0]]
        res = []
        # Start from East
        direction = 0
        # Number of moves
        step = 1
        repeat = 2
        # Out of Bound check
        while len(res) < rows * cols:
            # Length of move increments after 2 moves
            for _ in range(repeat):
                # Validating each step
                for _ in range(step):
                    if (
                        rStart >= 0
                        and rStart < rows
                        and cStart >= 0
                        and cStart < cols
                    ):
                        res.append([rStart,cStart])
                    rStart += dir[direction][0]
                    cStart += dir[direction][1]
                direction = (direction + 1) % 4
            step += 1 
        return res
```

## Time Complexity
O(n * m)
> Iterates through every element in a 2D matrix

## Space Complexity
O(n * m)
> Initializes and returns every element in a 2D matrix
---