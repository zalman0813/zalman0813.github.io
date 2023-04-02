---
title: "1143. Longest Common Subsequence"
date: 2023-04-02T18:36:34+08:00
draft: false
tags: ["medium", "dp", "longest common subsequence"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/longest-common-subsequence/

Status: done

Solution: bottom-up

Code:
```python
# Time Complexity: O(m*n)
# Space Complexity: O(m*n)
class Solution:
    def longestCommonSubsequence(self, text1: str, text2: str) -> int:
        
        dp = [ [0 for j in range(len(text2)+1)] for i in range(len(text1)+1)]

        for i in range(1, len(text1)+1):
            for j in range(1, len(text2)+1):
                if text1[i-1] == text2[j-1]:
                    dp[i][j] = 1 + dp[i-1][j-1]
                else:
                    dp[i][j] = max(dp[i-1][j], dp[i][j-1])
        return dp[-1][-1]
```

