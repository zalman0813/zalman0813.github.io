---
title: "93. Restore Ip Addresses"
date: 2023-03-05T08:16:16+08:00
draft: false
tags: ["169", "medium", "backtracking"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/restore-ip-addresses/

Status: done

Solution: backtracking

Code:
```python
#Time Complexity: O(1)
#Space Complexity: O(1)

class Solution:
    def restoreIpAddresses(self, s: str) -> List[str]:
        if len(s) < 4 or len(s) > 12:
            return []
        result = []

        def backtracking(i, dots, curIp):
            if dots == 4 and i == len(s):
                result.append(curIp[:-1])
                return
            if dots > 4:
                return
            
            for j in range(i, min(i+3,len(s))):
                if int(s[i:j+1]) <= 255 and (i == j or s[i] != '0'):
                    backtracking(j+1, dots + 1, curIp + s[i:j+1] + ".")
        backtracking(0, 0, "")

        return result

```
