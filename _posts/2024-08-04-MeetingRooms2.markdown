---
layout: post
title: Meetings Rooms II
date: 2024-08-04
categories: leetcode python
---
## Problem
![alt text](/blog/public/img/MeetingRooms2.png)

## Approach


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
> If every intervals' time occupy within themselves, there has to be n rooms

---