---
title: "516. Longest Palindromic Subsequence"
date: 2023-04-09T16:52:54+08:00
draft: false
tags: ["medium", "dp", "lps"]
series: ["leetcode"]
categories: ["coding"]
---
Link: https://leetcode.com/problems/longest-palindromic-subsequence/description/


Code:
```python
# Time Complexity: O(n^2)
# Space Complexity: O(n^2)
class Solution:
    def longestPalindromeSubseq(self, s: str) -> int:
        dp = [[0 for j in range(len(s))] for i in range(len(s))]

        for i in range(len(s)):
            dp[i][i] = 1
        
        for i in range(len(s)-2, -1, -1):
            for j in range(i+1, len(s)):
                if j < i:
                    continue
                if s[i] == s[j]:
                    dp[i][j] = 2 + dp[i+1][j-1]
                else:
                    dp[i][j] = max(
                        dp[i+1][j],
                        dp[i][j-1]
                    )
        return dp[0][len(s)-1]

```





