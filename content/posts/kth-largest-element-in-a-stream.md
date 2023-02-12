---
title: "703. Kth Largest Element in a Stream"
date: 2023-02-12T15:12:46+08:00
draft: false
tags: ["top k elements", "minheap","easy"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/kth-largest-element-in-a-stream/description/

Solution: top k elements

Code:
```python
# Time Complexity: 
   # 1. init function - O(nlogn)
   # 2. add function - O(logk)
# Space Complexity: O(n)
import heapq
class KthLargest:

    def __init__(self, k: int, nums: List[int]):
        self.minHeap = nums
        self.k = k
        heapq.heapify(self.minHeap)
        while len(self.minHeap) > self.k:
            heappop(self.minHeap)

    def add(self, val: int) -> int:
        heappush(self.minHeap, val)
        if len(self.minHeap) > self.k:
            heappop(self.minHeap)
        return self.minHeap[0]

```

