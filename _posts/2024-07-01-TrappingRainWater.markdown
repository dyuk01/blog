---
layout: post
title: Trapping Rain Water
date: 2024-07-01
categories: leetcode python
---

## Problem
![alt text](/blog/public/img/TrappingRainWater.png)

## Approach


## Code
```python
class Solution(object):
    def trap(self, height):
        """
        :type height: List[int]
        :rtype: int
        """
        l = l_max = r_max = res = 0
        r = len(height) - 1
        while l <= r:
            if height[l] <= height[r]:
                if height[l] >= l_max:
                    l_max = height[l]
                else:
                    res += l_max - height[l]
                l += 1
            else:
                if height[r] >= r_max:
                    r_max = height[r]
                else:
                    res += r_max - height[r]
                r -= 1
        return res
```
## Time Complexity
O(n)
> 
## Space Complexity
O(1)
> 

---