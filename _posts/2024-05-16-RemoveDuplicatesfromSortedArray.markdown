---
layout: post
title: Remove Duplicates from Sorted Array
date: 2024-05-16
categories: leetcode python
---
## Problem
![alt text](/blog/public/img/RemoveDuplicatesfromSortedArray.png)

## Approach
This problem is similar to <a href="https://dyuk01.github.io/blog/leetcode/string/array/python/2024/05/15/RemoveElement.html">Remove Element</a> problem, but the difference is that specific value is not given  
since its goal is to find the duplicates.

0. Since the list is in increasing (non-decreasing) order, there is no need to order the list.  
This means that we can safely initialize index to 0 and become the starting point.
1. Because we are going to have index as our first element,  
we need to adjust the for loop to iterate from the second element to the end
2. Operate the following procedure while iterating through the array:
- If the current value is not the duplicate: 
- Increment index by 1
- Replace the non-duplicate element to the array
3. Return index incremented by 1 since we need to consider our first element in the array as well.

## Code
```python
class Solution(object):
    def removeDuplicates(self, nums):
        index = 0
        # Iterate the array from 2nd to end 
        for i in range(1, len(nums)) :
            # If the next element is not the duplicate, increment the index and add it to the array 
            if nums[i] != nums[index] :
                index += 1
                nums[index] = nums[i]
        # Return the number of elements in the array including the initial element
        return index + 1
```
## Time Complexity
O(n)
> Iterates through the array once 

## Space Complexity
O(1)
> Constant amount of extra space is used  

---