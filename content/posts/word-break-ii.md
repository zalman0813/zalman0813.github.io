---
title: "140. Word Break Ii"
date: 2023-04-02T18:41:31+08:00
draft: false
tags: ["medium", "dp", "longest common subsequence"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/word-break-ii/description/

Status: done

Solution: bottom-up

Code:
```python
# Time Complexity: O(n^2)
# Space Complexity: O(n^2)
class Solution:
    def wordBreak(self, s: str, word_dict: List[str]) -> List[str]:
        dp_solutions = [[]] * (len(s)+1)
        dp_solutions[0] = [""]

        for i in range(1, len(s)+1):
            temp = []
            for j in range(0, i):
                prefix = s[j:i]
                if prefix in word_dict:
                    for substrings in dp_solutions[j]:
                        temp.append((substrings + " " + prefix).strip())

            dp_solutions[i] = temp
        return dp_solutions[len(s)]
```


