---
layout: post
title: Crossing River
date: 2024-06-30
categories: programmers python
---

## Problem
![alt text](/blog/public/img/CrossingRiver.png)

## Translation
The "Niniz friends" from Kakao Elementary School are on an autumn picnic with "Ryan" the teacher when they encounter a stream with stepping stones. To ensure the "Niniz friends" can safely cross the stepping stones, "Ryan" the teacher establishes the following rules:

1. The stepping stones are arranged in a row, and each stepping stone has a number written on it. The number on each stepping stone decreases by 1 every time it is stepped on.
2. If the number on a stepping stone becomes 0, it can no longer be stepped on. At this point, you can jump over several stones to the next stone that can be stepped on.
3. If there are multiple possible stepping stones to jump to, always jump to the closest one.
4. The "Niniz friends" start on the left side of the stream and must reach the right side to be considered to have crossed the stream.
5. The "Niniz friends" cross the stream one at a time. Only after one friend has completely crossed the stream does the next friend start crossing.

Given an array stones representing the numbers on the stepping stones in sequence and an integer k representing the maximum number of stones that can be jumped over in one leap, write a function solution that returns the maximum number of friends that can cross the stepping stones.

## Approach
Because the stones has to be steppend as they are arranged, sort function cannot be used. In this case, using binary search and sliding window will be sufficient, since sliding window works best when there is a index restriction(consecutive index, etc.) and we are finding a maximum number of friends within a 2-d array.

## Code
```python
def solution(stones, k):
    # Check if pivot(middle) freind can cross the river
    # Sliding Window
    def canCross(mid):
        count = 0
        for stone in stones:
            if stone - mid < 0:
                count += 1
                if count >= k:
                    return False
            else:
                count = 0
        return True
    # Checks the maximum number of friends that can cross the road
    # Binary Search
    l,r = 1,max(stones)
    res = l
    while l <= r:
        mid = (l + r) // 2
        if canCross(mid):
            res = mid
            l = mid + 1
        else:
            r = mid - 1
    return res
```
## Time Complexity
O(M log(n))
> Binary search takes O(log n), where sliding window approach takes O(M(length of 'stones')). Since the algorithm uses both to find the maximum number of friends, the overall time complexity would be O(M log(n))

## Space Complexity
O(M)
> Traverses through the 'stones' array to access each stone during the sliding windows process.

---