---
layout: post
title: House Robber
date: 2024-06-20
categories: leetcode python
---

## Problem
![alt text](/blog/public/img/HouseRobber.png)

## Approach
The method is to have 2 variables (total money if a robber robbed the house, and total money if a robber did not rob the house, but the house next to it), and consistently compare each variables as the robber goes through each houses. This works because of max function, where it automatically searches for the most profit from the houses.

1. Initialize 4 variables (Current money before robbing a house, Current money without robbery, Money after robbing a house, Money after not robbing a house)
2. Find the maximum of current money, and pass it to variables with money after the robbery

## Code
```python
class Solution(object):
    def rob(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        rob = noRob = 0
        # Goes through the houses, and find the total money for robbed houses and total money for houses that did not get robbed.
        for num in nums:
            newRob = noRob + num
            newNoRob = max(noRob, rob)
            rob = newRob
            noRob = newNoRob
        return max(rob, noRob)   
```

## Time Complexity
O(n)
> Goes through the input array exactly once 

## Space Complexity
O(1)
> Initializes int variables that do not corresponds to the length of the input

---