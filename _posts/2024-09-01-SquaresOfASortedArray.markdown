---
layout: post
title: Squares of a Sorted Array
date: 2024-09-01
categories: leetcode python
---
## Problem
![alt text](/blog/public/img/SquaresOfASortedArray.png)

## Approach
The goal is to return a list of squared integers of an input elements. However, the time complexity should be O(n), which limits us from simply squaring every element and execute sort() function. We cannot start from the middle and work up to the biggest element, since middle element cannot be always the smallest number as well. This is why I decided to get the maximum number to the smallest number, and reverse the whole list, which is still O(n)

## Code
```python
class Solution:
    def sortedSquares(self, nums: List[int]) -> List[int]:
        res = []
        l = 0 
        r = len(nums) - 1
        while l <= r:
            # Finds the maximum number between the both end, abs() was executed in case of negative integers
            if abs(nums[l]) <= abs(nums[r]):
                res.append(nums[r] ** 2)
                r -= 1
            else:
                res.append(nums[l] ** 2)
                l += 1
        return res[::-1]
```

## Time Complexity
O(n)
> Iterates through each input elements exactly once

## Space Complexity
O(n)
> Squared input numbers are directly put into the result list, which is the length of the input size

---