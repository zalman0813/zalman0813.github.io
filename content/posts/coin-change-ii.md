---
title: "518. Coin Change Ii"
date: 2023-03-25T16:21:41+08:00
draft: false
tags: ["medium", "dp"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/coin-change-ii/description/

Status: done

Solution: dp-bottom up

Code:
```python
#Time Complexity: O(n*c), where c is amount
#Space Complexity: O(n*c)
class Solution:
    def change(self, amount: int, coins: List[int]) -> int:
        if amount == 0:
            return 1
        
        dp = [[1 for j in range(len(coins))] for i in range(amount+1) ]
        
        for amt in range(1, amount+1):
            for j in range(len(coins)):
                x = 0
                if amt - coins[j] >= 0:
                    x = dp[amt - coins[j]][j]
                y = 0
                if j >= 1:
                    y = dp[amt][j-1]
                dp[amt][j] = x + y
        return dp[amount][len(coins)-1]
```


```python
#Time Complexity: O(n*c), where c is amount
#Space Complexity: O(n)
class Solution:
    def change(self, amount: int, coins: List[int]) -> int:
        dp = [0] * (amount + 1)
        dp[0] = 1

        
        for coin in coins:
            for amt in range(1, amount + 1):
            if amt >= coin:
                dp[amt] += dp[amt - coin]
        return dp[amount]
```
