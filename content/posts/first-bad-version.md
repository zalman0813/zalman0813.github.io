---
title: "278. First Bad Version"
date: 2022-11-17T20:49:28+08:00
draft: false
tags: ["binary search", "169", "easy"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/first-bad-version/

Solution: binary search

Code:
```python
class Solution:
    def firstBadVersion(self, n: int) -> int:
        
        l, r = 1, n

        # Find whether the mid version is bad or not
        # keep r as m is True,
        # F, F, T ,T , T
        # l->   m      r
        #    l  r
        #    l->
        # l from false to true, so final l position as minBadVersion
        while l < r:
            m = l + (r-l) // 2 # avoid overflow
            if isBadVersion(m):
                r = m 
            else:
                l = m + 1
        return l
```

Time Complexity: O(logn)

Space Complexity: O(1)
