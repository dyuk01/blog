---
layout: post
title: Longest Substring Without Repeating Characters
date: 2024-06-07
categories: leetcode python
---

## Problem
![alt text](/blog/public/img/LongestSubstringWithoutRepeatingCharacters.png)

## Approach
Question that can be solved with <a href="https://www.geeksforgeeks.org/window-sliding-technique/" target="_blank">window sliding</a> technique. 

## Code
```python
class Solution(object):
    def lengthOfLongestSubstring(self, s):
        """
        :type s: str
        :rtype: int
        """
        string = ""
        length = 0
        maxLength = 0
        for i in range(len(s)):
            # Removes the first index of the string repeatedly until there is no repeating characters
            while s[i] in res:
                string = string[1:]
                length -= 1
            res += s[i]
            length += 1
            maxLength = max(length, maxLength)
        return maxLength
```

## Time Complexity
O(n)
> The loop iterates through each characters exactly once

## Space Complexity
O(n)
> Utilizes 'res', which depends on the length of the input string

---