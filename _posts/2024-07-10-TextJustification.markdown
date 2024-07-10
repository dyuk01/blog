---
layout: post
title: TextJustification
date: 2024-07-10
categories: leetcode python
---

## Problem
![alt text](/blog/public/img/TextJustification.png)

## Approach


## Code
```python
class Solution(object):
    def fullJustify(self, words, maxWidth):
        """
        :type words: List[str]
        :type maxWidth: int
        :rtype: List[str]
        """
        res, cur, num_of_letters = [], [], 0
        for w in words:
            if num_of_letters + len(w) + len(cur) > maxWidth:
                for i in range(maxWidth - num_of_letters):
                    # Given cur is a list and i is an index
                    length = len(cur)
                    # This avoids division by zero
                    if length > 1:
                        adjusted_length = length - 1
                    else :
                        adjusted_length = 1
                    adjusted_length = length - 1 if length > 1 else 1  
                    # Calculate the wrapping index
                    index = i % adjusted_length  
                    # Append a space to the string at the calculated index
                    cur[index] += ' '  
                res.append(''.join(cur))
                cur, num_of_letters = [], 0
            cur += [w]
            num_of_letters += len(w)
        return res + [' '.join(cur).ljust(maxWidth)]
```
## Time Complexity
O(n)
> Iterates through the array exactly once in order to find the two sum

## Space Complexity
O(n)
> As input size increases, the amount of integers that the hashmap needs to store increases as well

---