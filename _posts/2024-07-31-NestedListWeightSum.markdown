---
layout: post
title: Nested List Weight Sum
date: 2024-07-31
categories: leetcode python
---
## Problem
![alt text](/blog/public/img/NestedListWeightSum.png)

## Approach
Since the problem is asking for the integers with their inidivudal depth, we know that we have to approach this problem with dfs algorithm.  

For dfs, we need to make sure:
1. If each element is a list or an integer
> .isInteger() function will distinguish the elements

2. If the element is integer, we can add the integer to the sum with its depth
3. If the element is a list, we can traverse to another list with incremented depth

## Code
```python
class Solution(object):
    def depthSum(self, nestedList):
        """
        :type nestedList: List[NestedInteger]
        :rtype: int
        """
        def dfs(list, depth):
            sum = 0
            for num in list:
                if num.isInteger():
                    sum += num.getInteger() * depth
                else:
                    sum += dfs(num.getList(), depth + 1)
            return sum

        return dfs(nestedList, 1)
```

## Time Complexity
O(n)
> Iterates through the nested list exactly once

## Space Complexity
O(n)
> Dfs algorithm's depth will be algorithm's space complexity

---