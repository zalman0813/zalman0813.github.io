---
title: "1891. Cutting Ribbons"
date: 2023-03-12T22:15:29+08:00
draft: false
tags: ["medium", "dp"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/cutting-ribbons/

Status: done

Solution: dp-bottom up

Code:
```python
#Time Complexity: O(n*k), where k is sizes.length
#Space Complexity: O(n)
def count_ribbon_pieces(n, sizes):
    # create the array to store the results
    dp = [-1]*(n+1)
    dp[0] = 0
    # calculate the results for all combinations
    # and select the maximum
    for i in range(1, n+1):
      for c in sizes:
        if i-c >= 0 and dp[i-c] != -1:
          dp[i] = max(dp[i], 1 + dp[i-c])
    
    if dp[n] != -1:
        return dp[n]
    else:
        return -1

```

