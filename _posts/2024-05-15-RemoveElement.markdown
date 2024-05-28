---
layout: post
title: Remove Element
date: 2024-05-15
categories: leetcode String/Array python easy
---
## Problem
![alt text](/blog/public/img/RemoveElement.png)

## Approach
The goal is to remove a specific number from an int array  
To achieve this, we need to use <a href="https://dyuk01.github.io/blog/algorithm/2024/05/15/InPlaceAlgorithm.html">in-place algorithm</a>.  
0. To begin, value that needs to be removed will be called <span style="font-weight: bold;">val</span>
1. Initialize index to 0, which represents number of non-target elements in the array
2. Operate the following procedure while iterating through the array:
- If the current value is not <span style="font-weight: bold;">val</span> : 
- Replace the current value with non-<span style="font-weight: bold;">val</span> variables
- Increment index by 1
3. Return index

## Code
```python
class Solution(object):
    def removeElement(self, nums, val):
        index = 0
        for i in range(len(nums)) :
            if nums[i] != val :
                nums[index] = nums[i]
                index += 1
        return index
```
## Time Complexity
O(n)
> Iterates through the array once 

## Space Complexity
O(1)
> Constant amount of extra space is used  

---