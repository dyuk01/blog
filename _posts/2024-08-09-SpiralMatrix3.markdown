---
layout: post
title: Spiral Matrix III
date: 2024-08-09
categories: leetcode python
---
## Problem
![alt text](/blog/public/img/SpiralMatrix3.png)

## Approach


## Code
```python
class Solution(object):
    def permute(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """
        def dfs(self, nums, path, res):
            if not nums:
                res.append(path[:])
                return
                
            for i, num in enumerate(nums):
                path.append(num)
                dfs(self, nums[:i] + nums[i + 1:], path, res)
                path.pop()

        res = []
        dfs(self, nums, [], res)
        return res
```

## Time Complexity
O(n!)
> 

## Space Complexity
O(n)
> 
---