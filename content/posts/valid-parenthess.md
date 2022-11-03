---
title: "20. Valid Parenthess"
date: 2022-11-01T21:38:19+08:00
draft: False
tags: ["stack", "169", "easy", "hashmap"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/valid-parentheses/

Tags: 169, easy, stack

Status: Done


Solution: Stack

Code:
```python
class Solution:
    def isValid(self, s: str) -> bool:
        stack = []
        Map = {")": "(", "]": "[", "}": "{"}
        
        for char in s:
            if char in Map:
                if stack and stack[-1] == Map[char]:
                    stack.pop()
                else:
                    return False
            else:
                stack.append(char)
        return True if not stack else False
```

Time Complexity: O(n)

Space Complexity:O(n)