---
layout: post
title: Number Of Senior Citizens
date: 2024-08-01
categories: leetcode python
---
## Problem
![alt text](/blog/public/img/NumberOfSeniorCitizens.png)

## Approach


## Code
```python
class Solution(object):
    def countSeniors(self, details):
        """
        :type details: List[str]
        :rtype: int
        """
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
> Iterates through the nested list exactly once

## Space Complexity
O(1)
> 

---