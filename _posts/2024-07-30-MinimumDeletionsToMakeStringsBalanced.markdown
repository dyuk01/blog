---
layout: post
title: Minimum Deletions To Make Strings Balanced 
date: 2024-07-30
categories: leetcode python
---
## Problem
![alt text](/blog/public/img/MinimumDeletionsToMakeStringsBalanced.png)

## Approach
The main approach is to automatically determine whether to delete encountered 'b' so far, or to delete the encountered 'a'

## Code
```python
class Solution(object):
    def minimumDeletions(self, s):
        """
        :type s: str
        :rtype: int
        """
        res = bCount = 0
        for ch in s:
            if ch == 'a':
                res = min(bCount, res + 1)
            else:
                bCount += 1
        
        return res
```

## Time Complexity
O(n)
> Iterates through the input string exactly once

## Space Complexity
O(1)
> Returns a constant variable(int)

---