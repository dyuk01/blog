---
layout: post
title: Travel Island
date: 2024-06-22
categories: Programmers python
---

## Problem
![alt text](/blog/public/img/TravelIsland.png)

## Translation
Mary is looking at a map to prepare for a trip to a deserted island this summer. The map shows information about the sea and deserted islands. The map is a rectangular grid made up of 1x1 squares, and each square on the grid contains either an ‘X’ or a natural number between 1 and 9. ‘X’ on the map represents the sea, and numbers represent deserted islands. The land connected by up, down, left, and right directions forms one island. The number written on each square of the map indicates the amount of food available, and the sum of the numbers connected in the up, down, left, and right directions represents the maximum number of days one can stay on that island. Mary, who hasn’t decided which island to visit, wants to first find out the maximum number of days she can stay on each island and then decide which island to visit.  
<br>
Given a string array maps representing the map, complete the solution function that returns an array containing the maximum number of days one can stay on each island in ascending order. If there are no islands to stay on, return an array with -1.

## Approach


## Code

```python
```
## Time Complexity
O(nm)
> Each DFS call can run for O(nm) when there is food for every possible land, and loop runs for another (nm). Resulting total time complexity as O(nm)

## Space Complexity
O(nm)
> Each visited array, DFS stack, and island list initializes O(nm), resulting in O(3nm) which simplifies to O(nm)

---