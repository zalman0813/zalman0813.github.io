---
title: "2395. Find Subarrays With Equal Sum"
date: 2023-03-19T19:45:47+08:00
draft: false
tags: ["hash table", "easy"]
series: ["leetcode"]
categories: ["coding"]
---


```python
# Time Complexity: O(n)
# Space Complexity: O(k), numbers of sum

class Solution:
    def findSubarrays(self, nums: List[int]) -> bool:
        sums = set()
        for i in range(len(nums)-1):
            t = nums[i]+nums[i+1]
            if t in sums:
                return True
            else:
                sums.add(t)
        return False
```
