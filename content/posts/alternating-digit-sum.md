---
title: "6296. Alternating Digit Sum"
date: 2023-01-22T11:09:36+08:00
tags: ["contest", "easy", "math"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/contest/weekly-contest-329/problems/alternating-digit-sum/

Code:
```python
# Time Complexity: O(n)
# Space Complexity: O(1)
class Solution:
    def alternateDigitSum(self, n: int) -> int:
        sum = 0
        digit_num = 0
        sign = 1
        while n > 0:
            digit = n % 10
            n //= 10
            sum += sign*digit
            digit_num += 1
            sign *= -1
        
        return sum if digit_num % 2 == 1 else -sum
```






