---
title: "509. Fibonacci Number"
date: 2023-03-25T16:53:42+08:00
draft: false
tags: ["medium", "dp", "recursive numbers"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/fibonacci-number

Status: done

Solution: dp-bottom up

Code:
```python
#Time Complexity: O(n)
#Space Complexity: O(n)
class Solution:
    def fib(self, n: int) -> int:
        if n == 0:
            return 0
        if n == 1:
            return 1
        dp = [0] * (n + 1)
        dp[0] = 0
        dp[1] = 1
        for i in range(2, n+1):
            dp[i] = dp[i-1] + dp[i-2]
        return dp[n]
```

```python
#Time Complexity: O(n)
#Space Complexity: O(1)
class Solution:
    def fib(self, n: int) -> int:
        if n == 0:
            return 0
        if n == 1:
            return 1
        prev_2 = 0
        prev_1 = 1
        for i in range(2, n+1):
            tmp = prev_1 + prev_2
            prev_2 = prev_1
            prev_1 = tmp 
        return prev_1
```