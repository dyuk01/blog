---
layout: post
title: Valid Palindrome
date: 2024-06-03
categories: leetcode two_pointers python
---

## Problem
![alt text](/blog/public/img/ValidPalindrome.png)

## Approach
Goal is to find if an input string provided is a palindrome or not. This is done after "converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters", which means that there should be only alphabets and numeric values.

1. Convert the input string into alphanumeric string
2. Start from start and end, and continue the loop until they meet at the middle

## Code
```python
class Solution(object):
    def isPalindrome(self, s):
        # Transforms an input string input alphanumeric string
        result = ''.join([char.lower() for char in s if char.isalnum()])

        # Left and Right pointers to keep track of Palindrome's validity
        l = 0
        r = len(result) - 1

        while l < r:
            # If the string is not mirrored, return False
            if result[l] != result[r]:
                return False
            # Next Iteration
            l += 1
            r -= 1
        return True
```

## Time Complexity
O(n)
> The loop always checks for the length of string once

## Space Complexity
O(n)
> Initializing the return value takes up to n (length of input string). Thus, resulting in O(n)

## Possible Improvement
Initializing result won't be necessary, since we can check the characteristics of palindrome inside the while loop with .isalnum() and .islower() with s[l] and s[r]

---