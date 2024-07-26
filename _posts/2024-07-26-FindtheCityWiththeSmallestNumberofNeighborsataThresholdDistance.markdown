---
layout: post
title: Find the City With the Smallest Number of Neighbors at a Threshold Distance
date: 2024-07-25
categories: leetcode python
---
## Problem
![alt text](/blog/public/img/FindtheCityWiththeSmallestNumberofNeighborsataThresholdDistance.png)

## Approach
Because we have to find all combinations to form a target number, we will use dfs to find all possible combinations to form the 'target' number

1. Initialize dfs
> Consisted of 4 variables. 'candidates', 'target', 'combination', and 'res'  
'candidates' and 'target' variables are from given problem, 'combination' is a series of numbers that form a 'target' number one set of combination that will be appended to 'res' when correct combination is found

## Code
```python
class Solution(object):
    def findTheCity(self, n, edges, distanceThreshold):
        """
        :type n: int
        :type edges: List[List[int]]
        :type distanceThreshold: int
        :rtype: int
        """
        dist = [[float('inf')] * n for _ in range(n)]
        # Initialize Node
        for node in range(n):
            dist[node][node] = 0
        # Set the values for the nodes
        for source, dest, weight in edges:
            dist[source][dest] = weight
            dist[dest][source] = weight
        
        # Pivot
        for i in range(n):
            # Node 1
            for j in range(n):
                # Node 2
                for k in range(n):
                    # Calculates distance from pivot to node 2
                    dist_total = dist[j][i] + dist[i][k]
                    # Found minimum path
                    if dist_total < dist[j][k]:
                        dist[j][k] = dist_total
                        dist[k][j] = dist_total
        
        min_city, min_path = None, float('inf')
        for node1 in range(n):
            node1_path = 0
            for node2 in range(n):
                # Found min_path
                if dist[node1][node2] <= distanceThreshold:
                    node1_path += 1
            if node1_path <= min_path:
                min_city = node1
                min_path = node1_path
        
        return min_city
        

        
```

## Time Complexity
O(n)
> 

## Space Complexity
O(1)
> 

---