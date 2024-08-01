---
layout: post
title: Number Of Senior Citizens
date: 2024-08-01
categories: leetcode python
---
## Problem
![alt text](/blog/public/img/NumberOfSeniorCitizens.png)

## Approach
The only information that matters within the given detail is the two numbers after a character. Since the details' length is 15, we can safely hard-code the age's index (11, 12)

## Code
```python
class Solution(object):
    def countSeniors(self, details):
        """
        :type details: List[str]
        :rtype: int
        """
        '''
        First attempt of solving the problem.
        1. Although this returns the right answer, its' time complexity (O(2n)), and space complexity (O(n)) are inferior to the new answer
        '''
        # ans = 0
        # res = [item[11:13] for item in details]
        # for age in res:
        #     if int(age) > 60:
        #         ans += 1
        # return ans
        
        ans = 0
        for info in details:
            if int(info[11:13]) > 60:
                ans += 1
        return ans
```

## Time Complexity
O(n)
> Iterates through the array exactly once

## Space Complexity
O(1)
> Returns

---