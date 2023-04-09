---
title: "72. Edit Distance"
date: 2023-04-09T17:46:33+08:00
draft: false
tags: ["hard", "dp", "lcs"]
series: ["leetcode"]
categories: ["coding"]
---
Link: https://leetcode.com/problems/edit-distance/description/


Code:
```python
# Time Complexity: O(n^2), where n is the length of the longest string.
# Space Complexity: O(n^2)
class Solution:
    def minDistance(self, str1: str, str2: str) -> int:

        dp = [[-1 for i in range(len(str2) + 1)] for j in range(len(str1)+1)]
        
        for i in range(len(str1)+1):
            dp[i][0] = i
        for j in range(len(str2)+1):
            dp[0][j] = j
        
        for i in range(1, len(str1)+1):
            for j in range(1, len(str2)+1):
                if str1[i-1] == str2[j-1]:
                    dp[i][j] = dp[i-1][j-1]
                else:
                    dp[i][j] = 1 + min(
                        dp[i-1][j-1], # replace
                        dp[i][j-1], # deletion
                        dp[i-1][j] # insertion
                    )
        return dp[-1][-1]
```
