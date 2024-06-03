---
layout: post
title: Valid Palindrome
date: 2024-06-03
categories: leetcode two_pointers python
---

## Problem
![alt text](/blog/public/img/ValidPalindrome.png)

## Approach


## Code
```python
class RandomizedSet(object):

    def __init__(self):
        self.list = []
        self.map = {}

    def insert(self, val):
        """
        :type val: int
        :rtype: bool
        """
        if val in self.list:
            return False
        self.list.append(val)
        self.map[val] = len(self.list) - 1
        return True

    def remove(self, val):
        """
        :type val: int
        :rtype: bool
        """
        if val not in self.list:
            return False
        last_element = self.list[-1]
        remove_element = self.map[val]
        self.map[last_element] = remove_element
        self.list[remove_element] = last_element
        self.list[-1] = val
        self.list.pop()
        self.map.pop(val)
        return True
        

    def getRandom(self):
        """
        :rtype: int
        """
        return random.choice(self.list)
        


# Your RandomizedSet object will be instantiated and called as such:
# obj = RandomizedSet()
# param_1 = obj.insert(val)
# param_2 = obj.remove(val)
# param_3 = obj.getRandom()
```

## Time Complexity
O(n)
> 

## Space Complexity
O(n)
>  

---