---
title: "373. Find K Pairs With Smallest Sums"
date: 2023-02-05T21:28:17+08:00
draft: false
tags: ["K-way merge", " medium"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/find-k-pairs-with-smallest-sums

Solution: K-way merge

Code:
K-way merge

```python

# Time Complexity: O(mlogm + klogm) -> (m + k)logm
# Space Complexity: O(m), where m = min(k, n1)
class Solution:
    def kSmallestPairs(self, nums1: List[int], nums2: List[int], k: int) -> List[List[int]]:
            result = []
            minHeap = []
            # pop & push
            for i in range(min(k,len(nums1))):
                heappush(minHeap, (nums1[i]+nums2[0], i, 0))
            counter = 1
            while counter <= k and minHeap:
                _, i1, i2 = heappop(minHeap)
                result.append((nums1[i1], nums2[i2]))
                i2 += 1
                if i2 < len(nums2):
                    heappush(minHeap, (nums1[i1]+nums2[i2], i1, i2))
                counter += 1
            return result

```


