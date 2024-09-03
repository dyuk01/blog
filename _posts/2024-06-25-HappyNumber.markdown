---
layout: post
title: Happy Number
date: 2024-06-25
categories: leetcode python
---

## Problem
![alt text](/blog/public/img/SearchInsertPosition.png)

## Approach
The goal is to validate whether the input is happy number or not. Because the code checks for infinite loop, I will be using while True in order to implement infinite loop

1. Since each digit has to be checked and squared in order to find the happy number, convert int to string
2. Having same result while looping means it is an unhappy number(infinite loop)
> Return False when this happens

3. Having sum as 1 means happy number
> Return True

## Code
```python
class Solution(object):
    def isHappy(self, n):
        """
        :type n: int
        :rtype: bool
        """
        num = n
        visited = []
        # Squares each integer and adds it to the total sum.
        while True:
            digits = str(num)
            res = 0
            for d in digits:
                res += int(d) ** 2
            num = res
            # Having same results mean infinite loop --> Unhappy loop
            if num in visited:
                return False
            visited.append(num)
            # Found 1 --> Happy Number
            if num == 1:
                break
        return True        
```
## Time Complexity
O(nlogn)
> Converting int to str takes about O(logn). However, the iteration increases with the input, resulting in O(nlogn)

## Space Complexity
O(n)
> Initializing 'visited' in order to check for infinite loop increases with the input

---