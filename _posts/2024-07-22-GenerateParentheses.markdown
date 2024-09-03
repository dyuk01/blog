---
layout: post
title: Generate Parentheses
date: 2024-07-22
categories: leetcode python
---
## Problem
![alt text](/blog/public/img/GenerateParentheses.png)

## Approach
The goal is to find all possible combination of the parentheses. In order to find every possible combination, we must use DFS to traverse through the combinations and return the suitable answers. For dfs, we must follow 3 crucial steps:

1. If the combination reaches its' maximum length (n * 2), return the combination to the answer  
2. Add '(' up to n times  
3. Add ')' only after '(' exist, and no more than '(' amount


## Code
```python
class Solution(object):
    def generateParenthesis(self, n):
        """
        :type n: int
        :rtype: List[str]
        """
        res = []
        def dfs(left, right, s):
            # Maximum length reached. Return the combination
            if len(s) == n*2:
                res.append(s)
                return
            # Append '('
            if left < n:
                dfs(left + 1, right, s + '(')
            # Append ')'
            if right < left:
                dfs(left, right + 1, s + ')')
        # Start dfs
        dfs(0,0,'')
        return res
```

## Time Complexity
O(4<sup>n</sup> / n<sup>3/2</sup>)
> The time complexity is derived from the n-th <a href="https://en.wikipedia.org/wiki/Catalan_number">Catalan Number</a>, which approximates to 4<sup>n</sup> / n<sup>3/2</sup>

## Space Complexity
O(n)
> The space complexity is determined by the depth of the recursion tree, which is n in the worst case

---