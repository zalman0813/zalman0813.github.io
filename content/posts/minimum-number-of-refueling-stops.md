---
title: "871. Minimum Number of Refueling Stops"
date: 2023-03-19T18:25:11+08:00
draft: false
tags: ["hard", "dp"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/minimum-number-of-refueling-stops/description/

Status: done

Solution: dp-bottom up

Code:
```python
#Time Complexity: O(n^2)
#Space Complexity: O(n^2)
class Solution:
    def minRefuelStops(self, target: int, startFuel: int, stations: List[List[int]]) -> int:
        n = len(stations)
        dp = [ [0]*(n+1) for _ in range(n+1) ]

        i = 0

        while i <= n:
            dp[i][0] = startFuel
            i += 1
        
        i = 1
        while i <= n:
            j = 1
            while j <= i:
                if dp[i-1][j-1] >= stations[i-1][0]:
                    dp[i][j] = max(dp[i-1][j], dp[i-1][j-1] + stations[i - 1][1])
                else:
                    dp[i][j] = dp[i-1][j]
                j += 1
            i += 1
        i = 0
        while (i <= n):
            if dp[n][i] >= target:
                return i
            i += 1
        return -1

```

