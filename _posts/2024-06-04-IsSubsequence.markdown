---
layout: post
title: Is Subsequence
date: 2024-06-04
categories: leetcode two_pointers python
---

## Problem
![alt text](/blog/public/img/IsSubsequence.png)

## Approach
The method is to iterate through the original string, and increment the subsequent string by 1 each time it finds a character in the input string. This way, we don't have to iterate through the original string multiple times for each letter in subsequent array.

## Code
```python
class Solution(object):
    def isSubsequence(self, s, t):
        """
        :type s: str
        :type t: str
        :rtype: bool
        """
        index = 0
        # Nothing to compare. Return True
        if len(s) == 0:
            return True
        # Iterate through the input string
        for c in t:
            # Increment the subsequent character if found in string array, and return True if all subsequent characters are found
            if s[index] == c:
                index += 1
                if index == len(s):
                    return True
        return False
```

## Time Complexity
O(n)
> The loop iterates through the array once

## Space Complexity
O(1)
> Only new variable initialized is 'index', which is an int variable(fixed amount). Resulting of O(1)

---