---
title: "1137. N Th Tribonacci Number"
date: 2023-03-26T08:29:59+08:00
draft: false
tags: ["easy", "dp", "recursive numbers"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/n-th-tribonacci-number/description/

Status: done

Solution: dp-bottom up

Code:
```python
#Time Complexity: O(n)
#Space Complexity: O(1)
class Solution:
    def tribonacci(self, n: int) -> int:
        if n == 0:
            return 0
        if n <= 2:
            return 1
        tn0 = 0
        tn1 = 1
        tn2 = 1

        for i in range(3, n+1):
            tmp = tn0 + tn1 +tn2
            tn0 = tn1
            tn1 = tn2
            tn2 = tmp
        return tmp
```
