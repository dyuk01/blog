---
layout: post
title: Rotate Array
date: 2024-05-17
categories: leetcode python
---
## Problem
![alt text](/blog/public/img/RotateArray.png)

## Approach
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
![alt text](/blog/public/img/RotateArrayExplanation.png)  
Although the order that I understood does not exactly match with the image, I structued my code based on this explanation.  

1. First, make a reverse function
2. Initialize a pivot function
3. Reverse the whole array
4. Reverse the left side of the array
5. Reverse the right side of the array  

## Code
```python
class Solution(object):
    def reverse(self, nums, start, end) :
        # Stop when the array is fully reversed
        while start < end :
            # Makes a storage to store the array's initial element
            temp = nums[start]
            # Replaces end with beginning and increment the counters
            nums[start] = nums[end]
            nums[end] = temp
            start += 1
            end -= 1
    def rotate(self, nums, k):
        # Make a pivot
        k %= len(nums)
        # Reverse the whole array
        self.reverse(nums, 0, len(nums) - 1)
        # Reverse the left side of the array
        self.reverse(nums, 0, k-1)
        # Reverse the right side of the array
        self.reverse(nums, k, len(nums) - 1)
```
## Time Complexity
O(n)
> O(n) + O(k) + O(n-k), which reduces to O(n)
## Space Complexity
O(1)
> Constant amount of extra space is used  

---
