---
layout: post
title: Remove Duplicates from Sorted Array - 2
date: 2024-05-16
categories: leetcode String/Array python
---
## Problem
![alt text](/blog/public/img/RemoveDuplicatesfromSortedArray2.png)

## Approach
This problem is a bit more complicated version of <a href="https://dyuk01.github.io/blog/leetcode/string/array/python/2024/05/16/RemoveDuplicatesfromSortedArray.html">Remove Duplicates from Sorted Array</a> problem, but the difference is that one duplicate can be included in the array.  
In this case, we need to add few if statements to determine if the elements are duplicates.

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
        count = 0
        # Iterate the array from 2nd to end 
        for i in range(1, len(nums)) : 
            # If the next element is the duplicate, increment the count
            if nums[i] == nums[index] : 
                count += 1
            # If the next element is not the duplicate, reset count
            if nums[i] != nums[index] :
                count = 0
            # If there is more than one duplicate, skip adding to the array
            if count > 1 :
                continue
            # Add the element to the array and increment index
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