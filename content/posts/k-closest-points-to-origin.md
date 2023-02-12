---
title: "973. K Closest Points to Origin"
date: 2023-02-12T16:14:53+08:00
draft: false
tags: ["top K elements", "maxHeap", "medium"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/k-closest-points-to-origin/description/

Solution: top k elements
Code:
top k elements

```python

# Time Complexity: O(nlogk)
# Space Complexity: O(k)
import heapq

class Solution:
    def kClosest(self, points: List[List[int]], K: int) -> List[List[int]]:
        
        maxHeap = []

        for (x, y) in points:
            if len(maxHeap) == K:
                head_x = maxHeap[0][1][0]
                head_y = maxHeap[0][1][1]
                if self.distance(x, y) < self.distance(head_x, head_y):
                    heapq.heappop(maxHeap)
                    heapq.heappush(maxHeap, [-self.distance(x, y), (x, y)])
            else:
                heapq.heappush(maxHeap, [-self.distance(x, y), (x, y)])
        
        return [[point[0], point[1]] for dist, point in maxHeap]
    
    def distance(self, x, y):
        return (x*x + y*y)

```

