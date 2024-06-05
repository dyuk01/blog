---
layout: post
title: Ransom Note
date: 2024-06-05
categories: leetcode python
---

## Problem
![alt text](/blog/public/img/RansomNote.png)

## Approach
The problem is asking if there are certain amounts of characters in the input string. To solve this, we need to count the number of each characters in 'ransomNote' and compare it to 'magazine'. This problem can be efficiently solved with using <a href="https://docs.python.org/3/library/collections.html" target="_blank">counter</a> function. Since this function sorts each characters as a key, with their frequency as their value.

## Code
```python
class Solution(object):
    def canConstruct(self, ransomNote, magazine):
        """
        :type ransomNote: str
        :type magazine: str
        :rtype: bool
        """
        # Utilizes counter to sort each characters in ransomNote into a hash with their frequency as their value
        ch1, ch2 = Counter(ransomNote), Counter(magazine)
        # Ensures that the ransomNote can be constructed from the characters available in the magazine 
        if ch1 & ch2 == ch1:
            return True
        return False
```

## Time Complexity
O(n + m)
> Since Counter goes through length of 'ransomNote' and 'magazine', the overall iteration length will be n + m (length of ransomNote + magazine)

## Space Complexity
O(n + m)
> ch1 and ch2 that was initialized has length of 'ransomNote' and 'magazine', which is n + m

---