---
layout: post
title: Zigzag Conversion
date: 2024-05-31
categories: leetcode String/Array python
---

## Problem
![alt text](/blog/public/img/ZigzagConversion.png)

## Approach


## Code
```python
class Solution(object):
    def convert(self, s, numRows):
        """
        :type s: str
        :type numRows: int
        :rtype: str
        """
        # If a letter is one character, return the original
        if numRows == 1:
            return s
        
        # Stores characters for each row
        L = [''] * numRows
        index, step = 0, 1

        # Move 
        for x in s:
            L[index] += x
            # If a character hit the ceiling, move down
            if index == 0:
                step = 1
            # If a character hi the floor, move up
            elif index == numRows -1:
                step = -1
            index += step

        return ''.join(L)     
```

## Time Complexity
O(n)
> 

## Space Complexity
O(1)
> 

---