---
layout: post
title: Length of Last Word 
date: 2024-05-23
categories: leetcode String/Array python easy
---
## Problem
![alt text](/blog/public/img/LengthofLastWord.png)

## Approach
The goal is to find the last word in a string that contains multiple spaces.

1. Use split function in python to safely acquire the words without the spaces
2. Return the length of the last word in the string array

## Code
```python
class Solution(object):
    def lengthOfLastWord(self, s):
        # Acquires series of words without any spaces
        words = s.split()
        # Returns the last word in the string array
        return len(words[-1])
```
## Time Complexity
O(n)
> split function goes through each character in the array, making the worst scenario O(n)

## Space Complexity
O(n)
> In the worst scenario, if the words in input array consists of only single characters, the list will contain n words  

---