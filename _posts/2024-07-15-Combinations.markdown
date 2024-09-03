---
layout: post
title: Combinations
date: 2024-07-15
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
            # Combination found
            if count == 0:
                res.append(list(combination))
            else:
                # Iterate from 1 to n
                for i in range(cur, n + 1):
                    # Add one number at a time
                    combination.append(i)
                    backtrack(count - 1, combination, i + 1)
                    # Reset combination
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