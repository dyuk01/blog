---
layout: post
title: 124 Number System
date: 2024-06-28
categories: programmers python
---

## Problem
![alt text](/blog/public/img/124NumberSystem.png)

## Translation
There is a country called 124 Country. In 124 Country, numbers are represented by their own unique system instead of the decimal system.

In 124 Country, only natural numbers exist.
In 124 Country, numbers are represented using only the digits 1, 2, and 4.
For example, the numbers in the 124 Country system are converted as follows:

| Decimal | 124 Country | Decimal | 124 Country |
| ---------- | ---------- | ---------- | ---------- |
| 1 | 1 | 6 | 14 |
| 2 | 2 | 7 | 21 |
| 3 | 4 | 8 | 22 |
| 4 | 11 | 9 | 24 |
| 5 | 12 | 10 | 41 |

Given a natural number 'n' as an input, please complete a solution function that converts 'n' to the corresponding number in the 124 Country system and returns it.

## Approach
Since the numbers that can be expressed is consisted of 3 numbers(1, 2, 4), dividing the input number by 3 and returning the remainder as an index of the 3 numbers initialized in the list will succesfully complete the conversion
1. Initialize the 124 number system vocab
2. Divide the number by 3, and return the remainder as the index of the vocab
3. Continue the loop until the input number is 0

## Code
```python
def solution(n):
    # 124 Number System
    numVocab = [4,1,2]
    res = ""
    # Returns the remainder(index of the number vocab) of a number after dividing by 3
    while n > 0:
        divide = n // 3
        rem = n % 3
        res = str(numVocab[rem]) + res
        if rem == 0 and divide > 0:
            divide -= 1
        n = divide            
    return res
```
## Time Complexity
O(n$\log_{3}{x}$)
> Iteration ends if the conversion is complete. If a number is large, the algorithm will go through more conversions since it will divide the number by 3 multiple times

## Space Complexity
O(n)
> Result increases as the number increases

---