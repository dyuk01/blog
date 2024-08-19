---
layout: post
title: Baseball Game
date: 2024-08-19
categories: leetcode python
---
## Problem
![alt text](/blog/public/img/BaseballGame.png)

## Approach
There are 3 characters that needs to be addressed in the code:  
'C' : Pop the stack  
'D' : Double the last element and push
'+' : Sum last and second last element and push  
Turning these into code will be sufficient

## Code
```python
class Solution(object):
    def calPoints(self, operations):
        """
        :type operations: List[str]
        :rtype: int
        """
        stack = []
        res = 0
        # Iterate through the input
        for ch in operations:
            if ch == 'C':
                stack.pop()
            elif ch == 'D':
                stack.append(stack[-1] * 2)
            elif ch == "+":
                stack.append(stack[-1] + stack[-2])
            else:
                stack.append(int(ch))

        # Sum the elements in stack
        for num in stack:
             res += num

        return res
```

## Time Complexity
O(n)
>  

## Space Complexity
O(n)
> Initializes a stack that can be as long as the input if no 'D' appears

---