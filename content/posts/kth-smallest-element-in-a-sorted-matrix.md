---
title: "378. Kth Smallest Element in a Sorted Matrix"
date: 2023-02-03T22:34:00+08:00
draft: false
tags: ["K-way merge", " medium"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/kth-smallest-element-in-a-sorted-matrix/description/

Solution: K-way merge

Code:
K-way merge

```python

# Time Complexity: O(nlogn+(klogn))=O((n+k)logn)
# Space Complexity: O(n*n)
class Solution:
    def kthSmallest(self, matrix: List[List[int]], k: int) -> int:
        # TODO: Write your code here
        minHeap = []
        # firstly, insert (first elemetn of list, index of fist element, list)
        for l in matrix:
            heappush(minHeap, (l[0], 0, l))


        for _ in range(k - 1):
            value, index, l = heappop(minHeap)
            index += 1
            if index < len(l):
                heappush(minHeap, (l[index], index, l))
        value, _, _ = heappop(minHeap)
        return value

```



