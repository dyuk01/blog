---
layout: post
title: Zigzag Conversion
date: 2024-05-31
categories: leetcode String/Array python
---

## Problem
![alt text](/blog/public/img/ZigzagConversion.png)

## Approach
Since the problem asks us to print out row by row, the approach was to make 'numRows' amount of arrays to print. By having multiple arrays, I could go back and forth to store arrays according to their zigzag order and just print them out by rows in the end.

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

        # Iterate through original array
        for x in s:
            L[index] += x
            # If a character hit the ceiling, move down
            if index == 0:
                step = 1
            # If a character hit the floor, move up
            elif index == numRows -1:
                step = -1
            index += step

        return ''.join(L)     
```

## Time Complexity
O(n)
> Iterates n amounts of input characters

## Space Complexity
O(n)
> Maximum space it takes O(numRows) with O(n) (length of input string). With join function also being O(n), the total space complexity for this code would be O(n)

---