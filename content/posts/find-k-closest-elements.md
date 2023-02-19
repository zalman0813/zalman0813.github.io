---
title: "658. Find K Closest Elements"
date: 2023-02-19T16:44:39+08:00
draft: false
tags: ["binary search", "medium"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/find-k-closest-elements/description/

Solution: binary search

```python

# Time Complexity: O(log(n-k))
# Space Complexity: O(1)
class Solution:
    def findClosestElements(self, arr: List[int], k: int, x: int) -> List[int]:
        l, r = 0, len(arr) - k

        while l < r:
            m = l + (r - l) // 2
            if x - arr[m] > arr[m+k] - x:
                l = m + 1
            else:
                r = m
        return arr[l:l+k]
```
