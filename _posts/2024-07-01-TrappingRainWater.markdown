---
layout: post
title: Trapping Rain Water
date: 2024-07-01
categories: leetcode python
---

## Problem
![alt text](/blog/public/img/TrappingRainWater.png)

## Approach
Initial approach was to use sliding window method to move left and right pointers from the beginning of the array to the end. However, this approach only works for heights with increasing order. Thus, I decided to use left and right pointers from starting from both ends

1. Initialize left and right pointers from both ends of the array
2. Compare both pointers and iterate through the array
> If left pointer's height is less/equal to the right pointer's height:  
1. Compare between left pointer's max and current left pointer's height.  
2. If current value is greater than the left max, update left max  
3. If current value is less than the left max, it means there is a space for water. Include to the result  
If right pointer's height is less/equal to the left pointer's height, do the same for right pointers/max.

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
            # Left height is less/equal to right height
            if height[l] <= height[r]:
                # Update l_max
                if height[l] >= l_max:
                    l_max = height[l]
                # Water detected. Add water
                else:
                    res += l_max - height[l]
                l += 1
            # Right height is less/equal to left height
            else:
                # Update r_max
                if height[r] >= r_max:
                    r_max = height[r]
                # Water detected. Add water
                else:
                    res += r_max - height[r]
                r -= 1
        return res
```
## Time Complexity
O(n)
> Iterates through the 'height' array exactly once
## Space Complexity
O(1)
> Returns an int variable that uses constant amount of space

---