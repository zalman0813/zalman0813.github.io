---
title: "Best Time to Buy and Sell Stock"
date: 2022-11-03T18:48:37+08:00
draft: false
tags: ["two pointer", "169", "easy"]
series: ["leetcode"]
categories: ["coding"]
---

Solution: two pointer

Code:
```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        maxP = 0
        l, r = 0, 1

        while r < len(prices):   
            profit = prices[r] - prices[l]
            if profit > 0:
                maxP = max(profit, maxP)
            else:
                l = r
            r += 1
        return maxP
```

Time Complexity: O(n)

Space Complexity: O(1)