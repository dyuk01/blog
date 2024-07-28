---
layout: post
title: Minimum Remove to Make Valid Parentheses
date: 2024-07-28
categories: leetcode python
---
## Problem
![alt text](/blog/public/img/MinimumRemovetoMakeValidParentheses.png)

## Approach
The method is simple. ')' cannot exist without '(' when reading from left to right, and '(' cannot exist without ')' when reading from left to right. During the iteration, remove any invalid parentheses.

1. Initialize a list
> Since strings are immutable, converting it to a list will make the replace much easier

2. Iterate input from left to right
> Remove any invalid ')' from the list

3. Iterate input from right to left
> Remove any invalid '(' from the list

4. Return valid output

## Code
```python
class Solution(object):
    def minRemoveToMakeValid(self, s):
        """
        :type s: str
        :rtype: str
        """
        # Convert into list 
        s = list(s)
        leftCount = rightCount = 0

        # Iterate from left to right
        for i in range(len(s)):
            if s[i] == '(':
                leftCount += 1
            if s[i] == ')':
                rightCount += 1
                # There are more ')' than '('. Remove invalid characters
                if rightCount > leftCount:
                    rightCount -= 1
                    s[i] = ''      
        
        # Iterate from right to left
        for i in range(len(s) - 1, -1, -1):
            # There are more '(' than ')'. Remove invalid characters
            if s[i] == '(' and leftCount > rightCount:
                leftCount -= 1
                s[i] = ''
        
        return ''.join(s)
```

## Time Complexity
O(n)
> Initializes a list, iterates the string twice(from left to right, and right to left), and joins the string all together which results in O(4n). This simplifies to O(n)

## Space Complexity
O(n)
> Converts string elements into a list

---