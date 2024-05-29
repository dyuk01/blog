---
layout: post
title: Integer to Roman
date: 2024-05-20
categories: leetcode String/Array python
---
## Problem
![alt text](/blog/public/img/IntegertoRoman.png)

## Approach
This problem is a reversed <a href="https://dyuk01.github.io/blog/leetcode/string/array/python/easy/2024/05/20/RomanToIntger.html">Roman to Integer</a> problem, where I have to return a string of Roman Integers after the number input.  
  
This is a brute-force algorithm that checks every possible value for an int to be translated into roman numerals.  

1. Check if the input number is greater than the highest number in the table(1000), then translate it to the character.  
2. Repeat the step until you have no numbers

```python
class Solution:
    def intToRoman(self, num: int):
        # Create an empty array to store Roman numerals
        s = ""
        '''
        Brute-force through the integer and convert them into Roman numerals
        Checks for 5 and 10s, also special cases(4 and 9s)
        If the algorithm finds the number that it's looking for, add the character
        to the array and subtract the equivalent amount from the number
        '''
        while num >= 1000:
            s += "M"
            num -= 1000
        if num >= 900:
            s += "CM"
            num -= 900
        if num >= 500:
            s += "D"
            num -= 500
        if num >= 400:
            s += "CD"
            num -= 400
        while num >= 100:
            s += "C"
            num -= 100
        if num >= 90:
            s += "XC"
            num -= 90
        if num >= 50:
            s += "L"
            num -= 50
        if num >= 40:
            s += "XL"
            num -= 40
        while num >= 10:
            s += "X"
            num -= 10
        if num >= 9:
            s += "IX"
            num -= 9
        if num >= 5:
            s += "V"
            num -= 5
        if num >= 4:
            s += "IV"
            num -= 4
        while num:
            s += "I"
            num -= 1
        return s
```
## Time Complexity
O(n)
> Depends on the number, since it returns linear to the input

## Space Complexity
O(n)
> Return string length is proportional to the size of num  

---