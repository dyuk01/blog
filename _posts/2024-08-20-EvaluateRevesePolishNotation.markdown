---
layout: post
title: Evaluate Reverse Polish Notation
date: 2024-08-20
categories: leetcode python
---
## Problem
![alt text](/blog/public/img/EvaluateRevesePolishNotation.png)

## Approach
Similar to Baseball Game, but it has more arithmetic operations and special conditions to make the result more difficult.  

The algorithm will only add the numerical values into the stack, and follow the formula if it detects the arithmetic operator. After the operation, the stack will delete the used numbers and insert the number after the operation

## Code
```python
class Solution(object):
    def evalRPN(self, tokens):
        """
        :type tokens: List[str]
        :rtype: int
        """
        stack = []
        process = res = 0
        for ch in tokens:
            if ch == '+':
                process = int(stack[-2]) + int(stack[-1])
            elif ch == '-':
                process = int(stack[-2]) - int(stack[-1])              
            elif ch == '*':
                process = int(stack[-2]) * int(stack[-1])             
            elif ch == '/':
                # Convert from float to int in order to avoid automatic negative truncation in python
                process = int(float(stack[-2]) / float(stack[-1]))
            else:
                # Number found. Add number to the stack
                stack.append(ch)
                continue
            # Delete the last 2 numbers and add the newly created number after the formula
            stack.pop()
            stack.pop()
            stack.append(str(process))         
        
        # Since there will only be one number present in the stack after the process, return the number(answer)
        return int(stack[0])
```

## Time Complexity
O(n)
> Iterates through the input list exactly once to return the answer

## Space Complexity
O(n)
> Initializes a stack that can be as long as the input if there are no arithmetic operations detected 

---