---
title: "115. Distinct Subsequences"
date: 2023-04-02T20:46:36+08:00
draft: false
tags: ["medium", "dp", "longest common subsequence"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/distinct-subsequences/description/

Status: done

Solution: bottom-up

Code:
```python
# Time Complexity:  O(m×n) , where  m is the length of str1 and n is the length of str2.
# Space Complexity:  O(m×n)
class Solution:
    def numDistinct(self, str1: str, str2: str) -> int:
        m = len(str1)
        n = len(str2)
        dp = [[0 for x in range(0, n + 1)] for x in range(0, m + 1)]

        for i in range(0, n + 1):
            dp[m][i] = 0

        for i in range(0, m + 1):
            dp[i][n] = 1
        
        for i1 in range(m - 1, -1, -1):
            for i2 in range(n - 1, -1, -1):
                if str1[i1] == str2[i2]:
                    dp[i1][i2] += dp[i1 + 1][i2 + 1] + dp[i1 + 1][i2]
                else:
                    dp[i1][i2] = dp[i1 + 1][i2]

        return dp[0][0]
```