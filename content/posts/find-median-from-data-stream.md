---
title: "295. Find Median From Data Stream"
date: 2023-01-15T19:28:37+08:00
draft: false
tags: ["two heap", "hard"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/find-median-from-data-stream

Solution:
    two heaps
Code:
```python
# Time Complexity: 
#   addNume: O(logn)
#   findMedian: O(1)
# Space Complexity: O(n)


from heapq import *
class MedianFinder:

    def __init__(self):
        self.maxHeap = []
        self.minHeap = []

    def addNum(self, num: int) -> None:

        if not self.maxHeap or -self.maxHeap[0] >= num:
            heappush(self.maxHeap, -num)
        else:
            heappush(self.minHeap, num)
        
        # more element than the min-heap
        # i.e. maxHeap [-5, -3, -1], minHeap [6, 7]
        if len(self.maxHeap) > len(self.minHeap) + 1:
            heappush(self.minHeap, -heappop(self.maxHeap))
        elif len(self.maxHeap) < len(self.minHeap):
            heappush(self.maxHeap, -heappop(self.minHeap))


    def findMedian(self) -> float:
        # we have even number of elements, take the average of middle two elements
        if len(self.maxHeap) == len(self.minHeap):
            return (-self.maxHeap[0] +  self.minHeap[0])/2

        else:
            return -self.maxHeap[0]
        


# Your MedianFinder object will be instantiated and called as such:
# obj = MedianFinder()
# obj.addNum(num)
# param_2 = obj.findMedian()
        
```

