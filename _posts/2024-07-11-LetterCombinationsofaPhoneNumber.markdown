---
layout: post
title: Letter Combinations of a Phone Number
date: 2024-07-11
categories: leetcode python
---

## Problem
![alt text](/blog/public/img/LetterCombinationsofaPhoneNumber.png)

## Approach
The problem asks us to find all possible combinations of characters for a given input string of digits, where each digit maps to a set of characters similar to the telephone buttons. This means we cannot predetermine the number of iterations needed, making recursion a suitable approach to loop through the algorithm until all possible combinations are found. Additionally, since each digit maps to multiple characters, a simple for loop is insufficient. By using a backtracking method, we can systematically explore all potential combinations with in order.

## Code
```python
class Solution(object):
    def letterCombinations(self, digits):
        """
        :type digits: str
        :rtype: List[str]
        """
        res = []

        # Return empty input
        if len(digits) <= 0:
            return res
        
        # Define characters for a phone number
        keyboard = {
            "2" : "abc",
            "3" : "def",
            "4" : "ghi",
            "5" : "jkl",
            "6" : "mno",
            "7" : "pqrs",
            "8" : "tuv",
            "9" : "wxyz"
        }

        # Use recursion to utilize back tracking
        def backtrack(combination, next_digit):
            # All combinations found. Forming the answer to return as an answer
            if not next_digit:
                res.append(combination)
            # There are more combinations to be found. Proceed to the next digit
            else:
                for letter in keyboard[next_digit[0]]:
                    backtrack(combination + letter, next_digit[1:])

        # Run Back tracking
        backtrack("", digits)
        return res
```
## Time Complexity
O(n * 4<sup>n</sup>)
> Appending and forming the combination string takes O(n) times. In addition, finding all the possible iterations would take O(4<sup>n</sup>) times due to 4 characters in one number

## Space Complexity
O(n * 4<sup>n</sup>)
> The iteration adds a letter every iteration, resulting the same process as time complexity

---