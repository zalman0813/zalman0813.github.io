---
title: "347. Top K Frequent Elements"
date: 2023-02-12T16:56:14+08:00
draft: false
tags: ["top K elements", "minHeap", "medium"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/top-k-frequent-elements/description/

Solution: top k elements
Code:
top k elements

```python

# Time Complexity: O(nlogk)
# Space Complexity: O(n+k)
from collections import Counter
import heapq
class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        num_freq = Counter(nums)
        minHeap = []
        for num, count in num_freq.items():
            if len(minHeap) == k:
                if count > minHeap[0][0]:
                    heapq.heappop(minHeap)
                    heapq.heappush(minHeap, (count, num))
            else:
                heapq.heappush(minHeap, (count, num))
        return [ num for count, num in minHeap ]
```

