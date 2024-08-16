---
layout: post
title: Spiral Matrix
date: 2024-08-16
categories: leetcode python
---
## Problem
![alt text](/blog/public/img/SpiralMatrix.png)

## Approach
This problem requires handling positions and checking for visited elements

1. Initialize 2d matrix just for checking visited elements
> Set 2D matrix just like the input matrix, filled with False. This will be converted to True when iterating through the input matrix

2. Set up direction
> Spiral Moves in order : East, South, West, and North

3. Iterate through the given matrix
> Ensure that the positions do not go out of bound

## Code
```python
class Solution(object):
    def spiralOrder(self, matrix):
        """
        :type matrix: List[List[int]]
        :rtype: List[int]
        """
        visited = [[False] * len(matrix[0]) for _ in range(len(matrix))]
        res = []
        i = j = 0
        move = 0

        # Spiral Order : East, South, West, North
        direction = [[0,1], [1,0], [0,-1], [-1,0]]
        move = 0

        while len(res) < len(matrix) * len(matrix[0]):
            # Add number in order
            if visited[i][j] == False:
                res.append(matrix[i][j])
                visited[i][j] = True
            
            # If next number in order does not exist or already has been added, change the direction
            if (i + direction[move][0] >= len(matrix) or 
            i + direction[move][0] < 0 or
            j + direction[move][1] >= len(matrix[0]) or
            j + direction[move][1] < 0 or
            visited[i + direction[move][0]][j + direction[move][1]] == True):
                move = (move + 1) % 4
            
            i += direction[move][0]
            j += direction[move][1]
        
        return res
```

## Time Complexity
O(n * m)
> Iterates through every element in given matrix, which is the length of rows * columns

## Space Complexity
O(n * m)
> Initializes 'visited' 2D matrix, which allocates same memory as the input matrix
---