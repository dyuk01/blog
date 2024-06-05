---
layout: post
title: Palindrome Number
date: 2024-05-29
categories: leetcode python
---

## Problem
![alt text](/blog/public/img/PalindromeNumber.png)

## Approach
In essence, we have to check the reversed number from the original to see if it's palindrome or not. Because the problem challenges the users to prohibit the use of string by saying, "Could you solve it without converting the integer to a string?" We have to reverse the integer without using any strings. To reverse the integer, I used :

1. Divide the number by 10 to get the last digit
2. Add the divided digit to the variable for reversed integer
3. Reversed integer will be multipled by 10 since the position of last integer has to be moved up by 1 unit.

## Code
```python
class Solution(object):
    def isPalindrome(self, x):
        temp = x
        res = 0
        # Negative numbers cannot be palindrome
        if x < 0:
            return False
        # Single digits are always palindrome
        elif x < 10:
            return True
        # Reverse numbers
        while temp > 0:
            digit = temp / 10
            rem = temp % 10
            res = (res * 10) + rem
            temp /= 10
        # Palindrome Check
        if x == res:
            return True
        return False  
```

## Time Complexity
O(n)
> Depends on the number of digits in integer n

## Space Complexity
O(1)
> Used fixed amount of space that does not rely on the length of integer n

---