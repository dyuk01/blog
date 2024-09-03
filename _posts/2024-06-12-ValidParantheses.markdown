---
layout: post
title: Valid Parantheses
date: 2024-06-12
categories: leetcode python
---

## Problem
![alt text](/blog/public/img/ValidParantheses.png)

## Approach
The input strings are only consisted of parentheses, which means there is no need for checking invalid characters. First, add push every opening parentheses('[{('), and check for the validiity when checking for the closing parentheses(')}]')

1. Initialize a stack
2. Push opening parentheses into a stack
3. When encountered with closing parentheses, compare with the top of the stack

## Code
```python
class Solution(object):
    def isValid(self, s):
        """
        :type s: str
        :rtype: bool
        """
        brac = []
        for ch in s:
            # Accept every opening parentheses
            if ch in '[{(':
                brac.append(ch)
            else:
                # If closing parentheses don't match with the opening parentheses, or there is no opening parentheses, return False
                if len(brac) == 0 or (ch == ')' and brac[-1] != '(') or \
                (ch == '}' and brac[-1] != '{') or \
                (ch == ']' and brac[-1] != '['):
                    return False
                brac.pop()
        return len(brac) == 0           
```

## Time Complexity
O(n)
> Only iterates through the string 's' once

## Space Complexity
O(n)
> Initializes the stack that can store at most length of s 

---