---
layout: post
title: Rotate Array
date: 2024-05-16
categories: leetcode String/Array python
---
## Problem
![alt text](/blog/public/img/MajorityElement.png)

## Approach


## Code
My original approach was to have nested for loop like below,
```python
class Solution(object):
    def rotate(self, nums, k):
        end = len(nums) - 1
        for i in range(k) :
            for j in range(end) :
                temp = nums[end]
                nums[end] = nums[j]
                nums[j] = temp 
```
but I soon realized this would have time complexity of O(n<sup>2</sup>), which is not an optimal code.

## Time Complexity
O(n)

## Space Complexity
O(1)
