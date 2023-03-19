---
title: "1277. Count Square Submatrices With All Ones"
date: 2023-03-19T17:09:18+08:00
draft: false
tags: ["medium", "dp"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/count-square-submatrices-with-all-ones/description/

Status: done

Solution: dp-bottom up

Code:
```python
#Time Complexity: O(n*m)
#Space Complexity: O(n*m)
class Solution:
    def countSquares(self, nums: List[List[int]]) -> int:

        rows = len(nums)
        cols = len(nums[0])

        dp = [ [0]*cols for i in range(rows) ]

        for i in range(rows):
            dp[i][0] = nums[i][0]

        for j in range(cols):
            dp[0][j] = nums[0][j]
        
        for i in range(1, rows):
            for j in range(1, cols):
                if nums[i][j] == 0:
                    continue
                dp[i][j] = 1 + min(dp[i-1][j], dp[i][j-1], dp[i-1][j-1])
        return sum([sum(row) for row in dp])

```
