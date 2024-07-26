---
layout: post
title: Find the City With the Smallest Number of Neighbors at a Threshold Distance
date: 2024-07-26
categories: leetcode python
---
## Problem
![alt text](/blog/public/img/FindtheCityWiththeSmallestNumberofNeighborsataThresholdDistance.png)

## Approach
We can identify that this problem is utilizing an undirected weighted graph in order to find the city with the fewest paths to other cities, given a distance threshold to limit the distance. I will be using the Floyd-Warshall Algorithm to find a city with the least number of neighbors.

1. Initialize distance with infinity
2. Set distance for each node to itself
3. Set initial distances based on edges
4. Floyd-Warshall Algorithm
> - Use each node as an intermediate point and update the distance matrix to find the shortest paths between every pair of nodes  
- If a shorter path is found through an intermediate node, update the distance accordingly
5. Determine the city with the smallest number of neighbors within the threshold

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
        # Information set
        for src, dest, weight in edges:
            dist[src][dest] = weight
            dist[dest][src] = weight
        # Pivot Node
        for i in range(n):
            # Source Node
            for j in range(n):
                # Destination Node
                for k in range(n):
                    # Find the shortest distance between the nodes
                    path_length = dist[j][i] + dist[i][k]
                    if path_length < dist[j][k]:
                        dist[j][k] = path_length
                        dist[k][j] = path_length

        # Find the least neighboring city
        min_city, min_path = None, float('inf')
        for node1 in range(n):
            node1_path = 0
            for node2 in range(n):
                if dist[node1][node2] <= distanceThreshold:
                    node1_path += 1
            if node1_path <= min_path:
                min_city = node1
                min_path = node1_path
        
        return min_city
```

## Time Complexity
O(n<sup>3</sup>)
> Uses 3 for loop(pivot, source, and destination node iteration) throughout the algorithm

## Space Complexity
O(n<sup>2</sup>)
> Initializes 'dist' which makes a 2D matrix for the possible weights between the cities

---