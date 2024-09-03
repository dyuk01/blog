---
layout: post
title: Climbing Stairs
date: 2024-06-18
categories: leetcode python
---

## Problem
![alt text](/blog/public/img/ClimbingStairs.png)

## Approach
1. Climbing 1 or 2 steps can also mean 'n - 1' and 'n - 2' steps
2. Set up base cases for only having 0, 1, and 2 steps
3. The answer will be the sum of ways to reach the n - 1 step and the n - 2 step

## Code
```python
class Solution(object):
    def climbStairs(self, n):
        """
        :type n: int
        :rtype: int
        """
        # Base Cases
        if n <= 0:
            return 0
        if n == 1:
            return 1
        if n == 2:
            return 2
        # Set up DP to efficiently solve the answer
        dp = [0] * (n + 1)
        # Set up Base case
        dp[1] = 1
        dp[2] = 2
        # Sum of total n - 1 and n - 2 steps taken to reach the destination
        for i in range(3, n+1):
            dp[i] = dp[i-1] + dp[i-2]
        return dp[n]
        
```

## Time Complexity
O(n)
> The only time taken is when the code fills the dp with the number of steps.

## Space Complexity
O(n)
> Initializes dp, which corresponds to the size of input(n)

---