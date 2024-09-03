---
layout: post
title: Meetings Rooms II
date: 2024-08-04
categories: leetcode python
---
## Problem
![alt text](/blog/public/img/MeetingRooms2.png)

## Approach
With given time intervals, we need to identify any overlapping intervals for determining the number of rooms required for the meetings.  
Initially, two pointer approach is what came to my mind, but I quickly realized utilizing min-heap will simplify the code by a significant amount compared to two pointer. Although they both have O(nlogn), the code becomes significantly longer for two pointers since I have to manually initialize start and end times and compare them individually

## Code
```python
import heapq
class Solution(object):
    def minMeetingRooms(self, intervals):
        """
        :type intervals: List[List[int]]
        :rtype: int
        """
        intervals.sort()
        heap = []
        for interval in intervals:
            # Room empty
            if heap and interval[0] >= heap[0]:
                heapq.heapreplace(heap, interval[1])
            # New room required
            else:
                heapq.heappush(heap, interval[1])
        return len(heap)
```

## Time Complexity
O(nlogn)
> Iterates through the list once, and uses heapreplace() and heappush(), which both takes O(nlogn)

## Space Complexity
O(n)
> If all meetings' interval overlaps, there has to be n rooms

---