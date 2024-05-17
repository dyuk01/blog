---
layout: post
title: Rotate Array
date: 2024-05-16
categories: leetcode String/Array python
---
## Problem
![alt text](/blog/public/img/RotateArray.png)

## Approach


## Code
My initial approach was to have nested for loop like below,
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
  
So, I tried pop and insert method to reduce time complexity.
```python
class Solution(object):
    def rotate(self, nums, k):
        for i in range(k):
            end = nums.pop()
            nums.insert(0, end) 
```
However, this method also did not pass the cases. Although the time complexity was reduced to O(kn),  
I assumed that the problem was looking for O(n) since there was a case with large array and k.  

I was lost at first, but soon realized how it works after looking at the solution.  
![alt text](/blog/public/img/RotateArraySolution.png)

## Time Complexity
O(n)

## Space Complexity
O(1)
