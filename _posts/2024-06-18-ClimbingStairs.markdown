---
layout: post
title: Climbing Stairs
date: 2024-06-18
categories: leetcode python
---

## Problem
![alt text](/blog/public/img/ClimbingStairs.png)

## Approach


## Code
```python
class Solution(object):
    def climbStairs(self, n):
        """
        :type n: int
        :rtype: int
        """
        if n <= 0:
            return 0
        if n == 1:
            return 1
        if n == 2:
            return 2
        dp = [0] * (n + 1)
        dp[1] = 1
        dp[2] = 2
        for i in range(3, n+1):
            dp[i] = dp[i-1] + dp[i-2]
        return dp[n]
        
```

## Time Complexity
O(n)
> Searching for starting point's coordinate needs to check every single space in 2d matrix

## Space Complexity
O(n)
> 

---