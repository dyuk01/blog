---
layout: post
title: Valid Parantheses
date: 2024-06-12
categories: leetcode python
---

## Problem
![alt text](/blog/public/img/ValidParantheses.png)

## Approach
Main goal is to give more candy to a child with a higher rating than the neighbor. Iterating through the array once with 2 pointers will not enough due to condition of the term 'neighbor' (check left and right). Thus, we have to iterate the array twice (Left->Right, Right->Left).

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
            if ch in '[{(':
                brac.append(ch)
            else:
                if len(brac) == 0 or (ch == ')' and brac[-1] != '(') or \
                (ch == '}' and brac[-1] != '{') or \
                (ch == ']' and brac[-1] != '['):
                    return False
                brac.pop()
        return len(brac) == 0           
```

## Time Complexity
O(n)
> Iterates through the array twice. O(n) + O(n) = O(2n), resulting in O(n)

## Space Complexity
O(n)
> Initializes the variable 'res', which is the length of the array

---