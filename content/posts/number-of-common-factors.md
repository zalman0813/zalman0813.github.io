---
title: "2427. Number of Common Factors"
date: 2023-03-12T22:18:47+08:00
draft: false
tags: ["easy", "math"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/number-of-common-factors/description/

Status: done

Solution: math

Code:
```python
#Time Complexity: O(n), where n is the smaller one in a, b
#Space Complexity: O(1)
class Solution:
    def commonFactors(self, a: int, b: int) -> int:
        if b > a:
            a, b = b, a

        count = 0
        for i in range(1, b+1):
            if a % i == 0 and b % i == 0:
                count += 1
        return count

```
