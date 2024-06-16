---
layout: post
title: Desktop Organization
date: 2024-06-15
categories: programmers python
---

## Problem
![alt text](/blog/public/img/DesktopOrganization.png)

## Translation
Meosseuk, who is preparing for a coding test, solves problems on Programmers and saves the written code anywhere on the computer desktop to review and study later. As the number of saved codes increases, Meosseuk thinks that his computer desktop has become too cluttered. Since he can revisit the problems on Programmers to see the code again, he decides to delete all the saved files.<br>

The computer desktop is represented as a grid where each cell is a square. The state of the desktop is given as a string array wallpaper. Files are located on the cells of the grid, and the grid points start from the top-left corner at (0, 0), represented as (row coordinate, column coordinate). An empty cell is represented by ".", and a cell with a file is represented by "#". By dragging, files can be selected and then deleted. Meosseuk wants to select all the files with a single drag that covers the minimum distance. The method of selecting files by dragging is as follows:<br>

Dragging involves clicking and holding the left mouse button on a grid point S(lux, luy) and moving to a grid point E(rdx, rdy) before releasing the left mouse button. This action is expressed as "dragging from point S to point E," with points S and E referred to as the start point and end point of the drag, respectively.<br>

The "dragging distance" when dragging from point S(lux, luy) to point E(rdx, rdy) is defined as |rdx - lux| + |rdy - luy|.<br>
When dragging from point S to point E, all files within the rectangle defined by the top-left point S and the bottom-right point E on the desktop grid are selected.

## Approach
1. The problem is asking for the minimum drag area
2. Navigate through the array, and find the coordinates of the files
3. Throughout the file's coordinates, we only have to drag from the minimum value of x and y to the maximum value of x and y

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
> Checks for every possible space for matrix while searching for the file

## Space Complexity
O(n)
> Initializes the space for storing x and y (O(2n)), which can be up to the length of the wallpaper in worst scenario.

## Possible Improvement
Although my code navigates through every space, I can iterate through the wallpaper only once with finding min and max value of x and y. This will reduce the time complexity to O(n)

---