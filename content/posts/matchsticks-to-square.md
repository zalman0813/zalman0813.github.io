---
title: "473. Matchsticks to Square"
date: 2023-03-05T23:26:52+08:00
draft: false
tags: ["169", "medium", "backtracking"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/matchsticks-to-square

Status: done

Solution: backtracking

Code:
```python
#Time Complexity: O(4^n)
#Space Complexity: O(n)
class Solution:
    def makesquare(self, matchsticks: List[int]) -> bool:
        tot_length = sum(matchsticks) 
        if tot_length % 4 != 0:
            return False
        
        length = tot_length / 4
        sides = [0]*4
        matchsticks.sort(reverse=True)
        def backtracking(i):
            if i == len(matchsticks):
                return True
            
            for j in range(4):
                if sides[j] + matchsticks[i] <= length:
                    sides[j] += matchsticks[i]
                    if backtracking(i+1):
                        return True
                    sides[j] -= matchsticks[i]
            return False
        return backtracking(0)

```
