---
layout: post
title: Zigzag Conversion
date: 2024-05-31
categories: leetcode string/array python
---

## Problem
![alt text](/blog/public/img/ZigzagConversion.png)

## Approach
Goal is to reverse a string without reversing the characters of the letters. This means that simply reversing the whole array will not work for this problem. In order to do this, we have to:
1. Remove any leading or trailing whitespace of the array
2. Seperate the words into different elements in string array
3. Reverse the string array
4. Put them back together seperated by space

## Code
```python
        
```

## Time Complexity
O(n)
> strip, split, reverse, and join function all runs for O(n) because they all iterate through each character in the array only once. Thus, the length of n in total. O(n) + O(n) + O(n) + O(n) = O(4n), which simplifies to O(n)

## Space Complexity
O(1)
> Because s was given as an input, modifying s to return as a output value does not impact the space complexity

---