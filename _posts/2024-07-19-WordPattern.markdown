---
layout: post
title: Word Pattern
date: 2024-07-19
categories: leetcode python
---
MergeIntervals
## Problem
![alt text](/blog/public/img/WordPattern.png)

## Approach


## Code
```python
class Solution(object):
    def wordPattern(self, pattern, s):
        """
        :type pattern: str
        :type s: str
        :rtype: bool
        """
        ch = {}
        word = {}
        words = s.split()

        # Checks for identical length
        if len(words) != len(pattern):
            return False
        
        # Groups each pattern with word
        for c,w in zip(pattern, words):
            if c not in ch:
                # If word is outside the pattern, return False
                if w in word:
                    return False
                # If both pattern and word is not in hashmap, add them
                else:
                    ch[c] = w
                    word[w] = c
            # If pattern is in hashmap, but word is different, return False
            else:
                if ch[c] != w:
                    return False
        return True
```
## Time Complexity
O(n + m)
> Iterates through 2 strings(pattern and s) exactly once, which makes the time complexity the sum of their length

## Space Complexity
O(n + m)
> Initializes 2 hashmaps for each pattern and word, which takes O(n + m) just like time complexity

---