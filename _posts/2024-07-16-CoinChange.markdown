---
layout: post
title: Coin Change 
date: 2024-07-16
categories: leetcode python
---

## Problem
![alt text](/blog/public/img/CoinChange.png)

## Approach


## Code
```python
class Solution(object):
    def coinChange(self, coins, amount):
        # Initialize DP array with a value greater than any possible solution
        dp = [float('inf')] * (amount + 1)
        dp[0] = 0  # Base case: 0 amount requires 0 coins

        # Track the coins used to achieve the solution
        coin_used = [-1] * (amount + 1)

        # Sort coins for consistent processing order
        coins.sort()

        # Fill the DP table
        for i in range(1, amount + 1):
            for j in range(len(coins) - 1, -1, -1):  # Process from last index to first
                if coins[j] <= i and dp[i - coins[j]] != float('inf'):
                    if dp[i] > dp[i - coins[j]] + 1:
                        dp[i] = dp[i - coins[j]] + 1
                        coin_used[i] = coins[j]

        # Check if it's possible to form the amount
        if dp[amount] == float('inf'):
            return -1

        # Build the solution using coin_used array
        result = []
        current_amount = amount
        while current_amount > 0:
            coin = coin_used[current_amount]
            result.append(coin)
            current_amount -= coin

        # Return the number of coins used and the coins themselves
        return len(result)
```

## Time Complexity
O()
> 

## Space Complexity
O()
> 

---