---
title: "70. Climbing Stairs"
date: 2023-03-12T22:19:10+08:00
draft: false
tags: ["easy", "dp"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/climbing-stairs/

Status: done

Solution: dp-bottom up

Code:
```python
#Time Complexity: O(n)
#Space Complexity: O(1)
class Solution:
    def climbStairs(self, n: int) -> int:
        one = 1
        two = 1
        
        # n = 5
        # [8,5,3,2,1,1] 4 times -> n - 1
        
        for i in range(n - 1):
            tmp = one
            one = one + two
            two = tmp
        return one

```

