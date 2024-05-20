---
layout: post
title: Roman to Integer
date: 2024-05-20
categories: leetcode String/Array python easy
---
## Problem
![alt text](/blog/public/img/RomantoInteger.png)

## Approach
For this problem, I deconstructed the Roman numeral system in order to decode them into numbers.

1. Make a translation chart with each symbol translated into numeric numbers
2. Decomposed the Roman Integer system by replacing the 4 and 9s into translatable symbols

## Code
```python
class Solution(object):
    def romanToInt(self, s):
        # Translation chart
        translations = {
            "I" : 1,
            "V" : 5,
            "X" : 10,
            "L" : 50,
            "C" : 100,
            "D" : 500,
            "M" : 1000
        }

        number = 0
        # Replacing all the 4 and 9s into readable characters
        s = s.replace("IV", "IIII").replace("IX", "VIIII")
        s = s.replace("XL", "XXXX").replace("XC", "LXXXX")
        s = s.replace("CD", "CCCC").replace("CM", "DCCCC")
        for char in s:
            # Translate the Roman integers
            number += translations[char]
        return number
        
```
## Time Complexity
O(n)
> .replace() takes O(n) times each, meaning the total time complexity is O(6n), which simplifies to O(n)

## Space Complexity
O(1)
> Constant amount of extra space is used