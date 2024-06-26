---
layout: post
title: Contains Duplicate II
date: 2024-06-26
categories: leetcode python
---

## Problem
![alt text](/blog/public/img/ContainsDuplicateII.png)

## Approach
Original approach was to use a type of sliding window in order to find the duplicates, and calculate the validity. However, this approach couldn't handle case with the first number not having any duplicates since the left pointer cannot move if there is no duplicate in the list.

```python      
class Solution(object):
    def containsNearbyDuplicate(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: bool
        """
        l, r = 0, 1
        while r < len(nums):
            if nums[l] == nums[r]:
                if r - l <= k:
                    return True
                l = r
            r += 1
        return False
```

## Code
This approach uses dictionary in order to store values and find the duplicates

1. Store the input values
2. If there are more than one identical inputs, it is counted as a duplicate
3. If a duplicate is met with the right condition, return True 

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
> Iterates through the input array exactly once

## Space Complexity
O(n)
> Initializes dictionary that can be as long as the input size

---