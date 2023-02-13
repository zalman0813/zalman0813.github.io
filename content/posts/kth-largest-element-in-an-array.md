---
title: "215. Kth Largest Element in an Array"
date: 2023-02-13T09:27:14+08:00
draft: false
tags: ["top K elements", "minHeap", "medium"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/kth-largest-element-in-an-array/description/

Solution: top k elements
Code:
top k elements

```python

# Time Complexity: O(nlogk)
# Space Complexity: O(k)
import heapq
class Solution:
    def findKthLargest(self, nums: List[int], k: int) -> int:
        # your code will replace this placeholder return statement
        minHeap = []

        for i in range(len(nums)):
            if len(minHeap) == k:
                if minHeap[0] < nums[i]:
                    heappop(minHeap)
                    heappush(minHeap, nums[i])
            else:
                heappush(minHeap, nums[i])


        return minHeap[0]
```
       

