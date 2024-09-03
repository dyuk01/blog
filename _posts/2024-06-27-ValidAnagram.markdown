---
layout: post
title: Valid Anagram
date: 2024-06-27
categories: leetcode python
---

## Problem
![alt text](/blog/public/img/ValidAnagram.png)

## Approach
The key aspect to keep in mind:
1. If the length is different, it cannot be an anagram
2. Number of used characters are the same. Just in different order

## Code
```python
class Solution(object):
    def isAnagram(self, s, t):
        """
        :type s: str
        :type t: str
        :rtype: bool
        """
        # Length different. Cannot be anagram
        if len(s) != len(t):
            return False
        # Look through both sets, and check if numbers of used characters are different
        for ch in set(s):
            if s.count(ch) != t.count(ch):
                return False
        return True
        
```
## Time Complexity
O(n)
> Looks through set(s), which increases with the input size 

## Space Complexity
O(1)
> Returns boolean, which does not increase with the input size

---