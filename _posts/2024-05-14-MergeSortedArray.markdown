---
layout: post
title: Merge Sorted Array
date: 2024-05-14
categories: leetcode String/Array python
---
## Problem
![alt text](/blog/public/img/MergeSortedArray.png)

## Approach
Since num1's size already accomodates m + n, we simply have to store variables of num2 into num1.   

## Code
```python
class Solution(object):
    def merge(self, nums1, m, nums2, n):
        for i in range(n):
            nums1[i + m] = nums2[i]
        nums1.sort()
```
## Time Complexity
O((m+n)log(m+n))
> Because this code uses sort function, the time complexity would be O(n log(n)).  
> However, since the code iterates through array size of m and n, the overall time complexity would be O((m+n)log(m+n)).

## Space Complexity
O(1)
> Constant amount of extra space is used  

---
