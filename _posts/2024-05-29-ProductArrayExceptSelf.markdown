---
layout: post
title: Product of Array Except Self 
date: 2024-05-29
categories: leetcode String/Array python
---

## Problem
![alt text](/blog/public/img/ProductArrayExceptSelf.png)

## Approach
Simple approach would be to multiply every elements in the array at first, and divide the current index's number. However, the problem prohibits using any division operation, which results more complicated thought process and answer. Original approach was to have nested for loop to iterate the array each time, but that would go against the policy of time complexity O(n). To optimize the solution, I divided the array to left and right side of pivot point, and multiply them together.
![alt text](/blog/public/img/ProductArrayExceptSelfImage.png)
1. Have left product of pivot point
2. Make another array of right product of pivot point, and multiply with left product to have the result
## Code
```python
class Solution(object):
    def productExceptSelf(self, nums):
        """
        :type nums: List[int]
        :rtype: List[int]
        """
        length = len(nums)
        # Set all arrays to 1(default)
        products = [1] * length
        # Calculate for product of pivot's left side
        for i in range(1, length):
            products[i] = products[i-1] * nums[i-1]
        right = nums[-1]
        # Calculate for product of pivot's right side, and multiply them into product of left pivot
        for i in range(length - 2, -1, -1):
            products[i] *= right
            right *= nums[i]
        return products    
```

## Time Complexity
O(n)
> Loop iterates through n 2 times, resulting in O(2n) which simplifies to O(n)

## Space Complexity
O(1)
> Original answer would be O(n), since we are initializing the size of an int array by n, but the problem states that "The output array does not count as extra space for space complexity analysis." in its follow-up statement. Thus, resulting in O(1)

---