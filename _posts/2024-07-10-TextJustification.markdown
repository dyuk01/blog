---
layout: post
title: TextJustification
date: 2024-07-10
categories: leetcode python
---

## Problem
![alt text](/blog/public/img/TextJustification.png)

## Approach
1. Add each word from 0 index. Distribute the empty spaces equally
> Since every word has to contain at least 1 space, add 1 each time the word is added

2. If the line reaches max width, proceed to the next line
> Calculate the capacity needed for empty space by maxWidth - number of total letters in one line  
Then, make sure to avoid zero division by setting the floor to 1.  
With the adjusted length, wrap the index

3. Return the left adjusted lines 

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
            # Max width exceeded. Distribute the empty spaces and proceed to the next line
            if num_of_letters + len(w) + len(cur) > maxWidth:
                for i in range(maxWidth - num_of_letters):
                    # Given cur is a list and i is an index
                    length = len(cur)
                    # Avoid zero division
                    if length > 1:
                        adjusted_length = length - 1
                    else :
                        adjusted_length = 1
                    # Calculate the wrapping index
                    index = i % adjusted_length  
                    # Append a space to the string at the calculated index
                    cur[index] += ' '  
                res.append(''.join(cur))
                cur, num_of_letters = [], 0
            # Insert the word
            cur += [w]
            num_of_letters += len(w)
        return res + [' '.join(cur).ljust(maxWidth)]
```
## Time Complexity
O(n * maxWidth)
> Loops through the words exactly once, which is O(n). However, since the code iterates through the characters while searching for the empty spaces, the result is O(n * maxWidth)

## Space Complexity
O(n)
> 

---