---
title: "131. Palindrome Partitioning"
date: 2023-04-09T18:02:21+08:00
draft: false
tags: ["169", "medium", "dp", "lps"]
series: ["leetcode"]
categories: ["coding"]
---
Link: https://leetcode.com/problems/palindromic-substrings/


Code:
```python
# Time Complexity: O(2^n)
# Space Complexity: O(2^n)
class Solution:
    def partition(self, s: str) -> List[List[str]]:
        dp = [[] for _ in range(len(s) + 1)]
        dp[-1] = [[]]
        for i in range(len(s) - 1, -1, -1):
            for j in range(i + 1, len(s) + 1):
                if s[i:j] == s[i:j][::-1]:
                    for item in dp[j]:
                        dp[i].append([s[i:j]] + item)
        return dp[0]

```

