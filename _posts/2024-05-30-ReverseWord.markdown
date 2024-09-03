---
layout: post
title: Reverse Word
date: 2024-05-30
categories: leetcode python
---

## Problem
![alt text](/blog/public/img/ReverseWord.png)

## Approach
Goal is to reverse a string without reversing the characters of the letters. This means that simply reversing the whole array will not work for this problem. In order to do this, we have to:
1. Remove any leading or trailing whitespace of the array
2. Seperate the words into different elements in string array
3. Reverse the string array
4. Put them back together seperated by space

## Code
```python
class Solution(object):
    def reverseWords(self, s):
        """
        :type s: str
        :rtype: str
        """
        # Remove front and end whitespace
        s = s.strip()
        # Seperate the string into series of words
        s = s.split()
        # Reverse the string
        s = s[::-1]
        # Merge the words into a string seperated by space.
        s = " ".join(s)

        return s
        
```

## Time Complexity
O(n)
> strip, split, reverse, and join function all runs for O(n) because they all iterate through each character in the array only once. Thus, the length of n in total. O(n) + O(n) + O(n) + O(n) = O(4n), which simplifies to O(n)

## Space Complexity
O(1)
> Because s was given as an input, modifying s to return as a output value does not impact the space complexity

---