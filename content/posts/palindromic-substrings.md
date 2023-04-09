---
title: "647. Palindromic Substrings"
date: 2023-04-09T16:57:04+08:00
draft: false
tags: ["169", "medium", "dp", "lps"]
series: ["leetcode"]
categories: ["coding"]
---
Link: https://leetcode.com/problems/palindromic-substrings/


Code:
```python
# Time Complexity: O(n^2)
# Space Complexity: O(n^2)
class Solution:
    def countSubstrings(self, str1: str) -> int:
        n = len(str1)

        lookup_table = [[False for _ in range(n)] for _ in range(n)]
        ps_count=0


        for i in range(n - 1, -1, -1):
            for j in range(i, n):
                if str1[i] == str1[j]:
                    if i+1 >= j:
                        lookup_table[i][j] = True
                    else:
                        lookup_table[i][j] = lookup_table[i+1][j-1]
                
                if lookup_table[i][j]:
                    ps_count += 1

        return ps_count

```

