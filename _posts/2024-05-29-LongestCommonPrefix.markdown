---
layout: post
title: Longest Common Prefix 
date: 2024-05-29
categories: leetcode python
---

## Problem
![alt text](/blog/public/img/LongestCommonPrefix.png)

## Approach
Since we have to find the longest common prefix, starting with the first word as prefix and removing the last character each time it does not equal to next elements will result in prefix.

## Code
```python
class Solution(object):
    def longestCommonPrefix(self, strs):
        """
        :type strs: List[str]
        :rtype: str
        """
        prefix = strs[0]

        # If two words don't match, exclude the last letter per loop
        for i in strs:
            while not i.startswith(prefix):
                prefix = prefix[:-1]

        return prefix   
```

## Time Complexity
O(nm)
> Loop iterates through the array once (O(n)). However, since we are going through the characters as well, the length of the longest string (O(m)) will take account as well. Resulting in O(n*m)

## Space Complexity
O(m)
> The length of the longest prefix(m) will be the space complexity

---