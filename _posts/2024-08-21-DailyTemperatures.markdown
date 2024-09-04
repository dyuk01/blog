---
layout: post
title: Daily Temperatures
date: 2024-08-21
categories: leetcode python
---
## Problem
![alt text](/blog/public/img/DailyTemperatures.png)

## Approach

## Code
```python
class Solution(object):
    def dailyTemperatures(self, temperatures):
        """
        :type temperatures: List[int]
        :rtype: List[int]
        """
        res = [0] * len(temperatures)
        stack = []

        for day, temp in enumerate(temperatures):
            while stack and temp > temperatures[stack[-1]]:
                prev_day = stack.pop()
                res[prev_day] = day - prev_day
            stack.append(day)
        return res
```

## Time Complexity
O(n)
> Iterates through the list exactly once

## Space Complexity
O(n)
> Initializes stack with 

---