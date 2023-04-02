---
title: "300.Longest Increasing Subsequence"
date: 2023-04-02T20:09:25+08:00
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
# Time Complexity: O(n^2)
# Space Complexity: O(n^2)
class Solution:
    def lengthOfLIS(self, nums: List[int]) -> int:
        
        size = len(nums)
        dp = [[0]*(size+1) for i in range(size+1)]

        for curr in range(size-1, -1, -1):
            for prev in range(curr-1, -2, -1):
                length = dp[curr+1][prev+1]
                if prev < 0 or nums[prev] < nums[curr]:
                    length = max(length, 1+dp[curr+1][curr+1])
                dp[curr][prev+1] = length
        return dp[0][0]
```

