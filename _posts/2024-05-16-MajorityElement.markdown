---
layout: post
title: Majority Element
date: 2024-05-16
categories: leetcode String/Array python easy
---
## Problem
![alt text](/blog/public/img/MajorityElement.png)

## Approach
The goal is to find the majority element of an array. Because there is an assumption that  
majority element always exist in the array, we can just return the position of floor(n/2)  
after sorting because majority element will always take more than half of the size of an array.

## Code
```python
class Solution(object):
    def majorityElement(self, nums):
        # Gets the length of array
        n = len(nums)
        # Sorts the array
        nums.sort()
        # Returns the element that is in position of floor (n/2)
        return nums[n/2]     
```
## Time Complexity
O(nlogn)
> Uses sort function 

## Space Complexity
O(1)
> Constant amount of extra space is used  

---