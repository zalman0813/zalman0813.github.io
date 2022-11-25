---
title: "67. Add Binary"
date: 2022-11-25T17:43:17+08:00
tags: ["bit", "169", "easy", "math"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/add-binary/

Code:
```python
# Time Complexity: O(n) or n(m), n - a.length, m - b.length 
# Space Complexity: O(n+m)
class Solution:
    def addBinary(self, a: str, b: str) -> str:
        
        res = ''
        carry = 0
        
        a = list(a)
        b = list(b)
        
        while a or b or carry:
            if a:
                carry += int(a.pop())
            if b:
                carry += int(b.pop())
            res += str(carry % 2)
            carry = carry // 2
        return res[::-1]
```




