---
layout: post
title: Desktop Organization
date: 2024-06-15
categories: programmers python
---

## Problem
![alt text](/blog/public/img/DesktopOrganization.png)

## Translation


## Approach
1. Identify starting position from the park layout.
2. Update position only if the movement is valid.
3. Return the final position of the robot dog.

## Code
```python
def solution(wallpaper):
    x = []
    y = []
    # Navigate through the array and find the file's position
    for i in range(len(wallpaper)):
        for j in range(len(wallpaper[i])):
            if wallpaper[i][j] == '#':
                x.append(j)
                y.append(i)
    
    answer = [min(y),min(x),max(y) + 1,max(x) + 1]
    return answer
```

## Time Complexity
O(n<sup>2</sup>)
> Searching for starting point's coordinate needs to check every single space in 2d matrix

## Space Complexity
O(1)
> Initializing variables throughout the algorithm only takes fixed amount of space (int variables)

---