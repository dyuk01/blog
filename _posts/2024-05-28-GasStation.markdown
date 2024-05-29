---
layout: post
title: Gas Station
date: 2024-05-28
categories: leetcode String/Array python medium
---

## Problem
![alt text](/blog/public/img/GasStation.png)

## Approach
As soon as I saw this problem, I could picture how the problem looked like. Since it is about travelling from one place to another with limited actions(fuel in this case) to check the possibility, this problem could be drawn into a weighted directed graph.  
![alt text](/blog/public/img/GasStationGraph.png)  
Although the graph doesn't have weights shown, assume this graph is weighted.

## Code
```python
class Solution(object):
    def canCompleteCircuit(self, gas, cost):
        """
        :type gas: List[int]
        :type cost: List[int]
        :rtype: int
        """
        # Total fuel to determine possibility of the travel
        total_fuel = 0
        # Fuel to determine if next travel is possible
        fuel = 0
        # Starting index of the travel
        index = 0
        for i in range(len(gas)):
            # Travel gas cost
            fuel += gas[i] - cost[i]
            total_fuel += gas[i] - cost[i]
            # Travel from ith to (i + 1)th gas station not possible. Move starting index to next iteration
            if fuel < 0:
                fuel = 0
                index = i + 1
        # Impossible trip
        if total_fuel < 0:
            return -1
        return index        
```

## Time Complexity
O(n)
> The loop runs n (length of list) times.

## Space Complexity
O(1)
> Uses fixed amount of space. 

---