---
title: "97. Interleaving String"
date: 2023-04-02T20:40:23+08:00
draft: false
tags: ["medium", "dp", "longest common subsequence"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/interleaving-string

Status: done

Solution: bottom-up

Code:
```python
# Time Complexity: O(s×t) where s and t are the lengths of s1 and s2, respectively
# Space Complexity: O(s×t) where s and t are the lengths of s1 and s2, respectively
class Solution:
    def isInterleave(self, s1: str, s2: str, s3: str) -> bool:
        if len(s1) + len(s2) != len(s3):
            return False

        dp = [[False for i in range(len(s2) + 1)] for i in range(len(s1) + 1)]

        for s1_index in range(len(s1) + 1):
            for s2_index in range(len(s2) + 1):

                if s1_index == 0 and s2_index == 0:
                    dp[s1_index][s2_index] = True
                elif s1_index == 0 and s2[s2_index - 1] == s3[s1_index + s2_index - 1]:
                    dp[s1_index][s2_index] = dp[s1_index][s2_index - 1]
                elif s2_index == 0 and s1[s1_index - 1] == s3[s1_index + s2_index - 1]:
                    dp[s1_index][s2_index] = dp[s1_index - 1][s2_index]
                else:
                    if s1_index > 0 and s1[s1_index - 1] == s3[s1_index + s2_index - 1]:
                        dp[s1_index][s2_index] = dp[s1_index - 1][s2_index]

                    if s2_index > 0 and s2[s2_index - 1] == s3[s1_index + s2_index - 1]:
                        dp[s1_index][s2_index] |= dp[s1_index][s2_index - 1]

        return dp[len(s1)][len(s2)]
```

