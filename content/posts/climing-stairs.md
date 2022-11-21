---
title: "70. Climing Stairs"
date: 2022-11-21T22:14:36+08:00
draft: false
tags: ["dp", "169", "easy"]
series: ["leetcode"]
categories: ["coding"]
---


Solution: dp - top down

Code:
```python
# Time Complexity: O(n)
# Space Complexity: O(1)
class Solution:
    def climbStairs(self, n: int) -> int:
        # DP: top-down
        # due to one step and two steps, 
        # (n-2)th result depends on the result of  n - 1, n
        # case n = 3, it's two way here,
        # two step: 1 -> -> 3
        # one step: 1 -> 2 
        
        # initiate one step, two step as 1. 
        # case n = 5
        # 0 - 1 - 2 - 3 - 4 - 5
        # (8   5   3   2) 1   1 --> caculate 4 times
        one = two = 1
        
        for i in range(n - 1):
            temp = one
            one = one + two
            two = temp
        return one
        
        
Time Complexity: O(n)
Space Complexity: O(1)

Link: https://leetcode.com/problems/climbing-stairs/



