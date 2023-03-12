---
title: "494. Target Sum"
date: 2023-03-12T21:45:23+08:00
draft: false
tags: ["medium", "dp"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/target-sum/description/

Status: done

Solution: dp-bottom up

Code:
```python
#Time Complexity: O(n*m), where m = sum(nums)
#Space Complexity: O(n)
class Solution:
    def findTargetSumWays(self, nums: List[int], target: int) -> int:
        tot = sum(nums)
        if tot < abs(target):
            return 0

        dp = [ [0 for j in range(2*tot + 1)] for i in range(len(nums))]

        dp[0][tot + nums[0]] = 1
        dp[0][tot - nums[0]] += 1

        for i in range(1, len(dp)):
            for t in range(-tot, tot+1):
                if dp[i-1][tot + t] > 0:
                    dp[i][tot + t - nums[i]] += dp[i-1][tot + t]
                    dp[i][tot + t + nums[i]] += dp[i-1][tot + t]
        return dp[len(nums) - 1][target + tot]

```
