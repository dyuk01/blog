---
layout: post
title: Combinations
date: 2024-07-14
categories: leetcode python
---

## Problem
![alt text](/blog/public/img/Combinations.png)

## Approach


## Code
```python
class Solution(object):
    def combine(self, n, k):
        """
        :type n: int
        :type k: int
        :rtype: List[List[int]]
        """
        res = []
        def backtrack(count, combination, cur):
            if count == 0:
                res.append(list(combination))
            else:
                for i in range(cur, n + 1):
                    combination.append(i)
                    backtrack(count - 1, combination, i + 1)
                    combination.pop()

        backtrack(k, [], 1)
        return res
```
## Time Complexity
O()
> 

## Space Complexity
O()
> 

---