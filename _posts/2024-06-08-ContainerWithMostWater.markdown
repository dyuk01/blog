---
layout: post
title: Container With Most Water
date: 2024-06-08
categories: leetcode python
---

## Problem
![alt text](/blog/public/img/ContainerWithMostWater.png)

## Approach
The goal is to find the maximum area of a rectangle within the int arrays. To do this, I need to figure out how to calculate the area without having such a high time complexity. Because it would take O(n<sup>2</sup>) to have nested for loop which checks every possible combination, we can use two pointers to only iterate the array once while still getting the answer.

## Code
```python
class Solution(object):
    def maxArea(self, height):
        """
        :type height: List[int]
        :rtype: int
        """
        l = 0
        r = len(height) - 1
        maxArea = 0
        # Goal is to find the maximum area of the rectangle(water) by using two pointers. By only moving the pointer that has lower height than other, we can safely find the largest amount of water within the container
        while l < r:
            area = min(height[l], height[r]) * (r - l)
            if height[l] > height[r]:
                r -= 1
            else:
                l += 1 
            maxArea = max(maxArea, area)
        return maxArea
```

## Time Complexity
O(n)
> The loop iterates through each element once

## Space Complexity
O(1)
> Only initializes int variables, which are irrelevent to the length of the array

---