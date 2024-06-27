---
layout: post
title: Valid Anagram
date: 2024-06-27
categories: leetcode python
---

## Problem
![alt text](/blog/public/img/ValidAnagram.png)

## Approach

## Code
```python
class Solution(object):
    def containsNearbyDuplicate(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: bool
        """
        lookup = {}
        
        for i in range(len(nums)):
            # If num is present in lookup and satisfy the condition return True
            if nums[i] in lookup and abs(dict[nums[i]]-i) <= k:
                return True
            # If num is not present in lookup then add it to lookup
            lookup[nums[i]] = i
        
        return False
```
## Time Complexity
O(n)
> 

## Space Complexity
O(1)
> 

---