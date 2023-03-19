---
title: "Number of Subsets"
date: 2023-03-19T20:00:29+08:00
draft: false
tags: ["medium", "dp"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://www.codingninjas.com/codestudio/problems/number-of-subsets_3952532?source=youtube&campaign=striver_dp_videos&utm_source=youtube&utm_medium=affiliate&utm_campaign=striver_dp_videos

Status: done

Solution: dp-bottom up

Code:
```python
#Time Complexity: O(n*s), where s is the target sum
#Space Complexity: O(n*s)
from os import *
from sys import *
from collections import *
from math import *

from typing import List

def findWays(nums: List[int], target_sum: int) -> int:
    # Replace this placeholder return statement with your code
    tot = sum(nums)
    if tot < target_sum:
        return 0
    dp = [ [0 for j in range(target_sum+1)] for i in range(len(nums))]
    # Base case 1
    if nums[0] == 0:
        dp[0][0] = 2
    # Base case 2
    else: 
        dp[0][0] = 1
        if nums[0] <= target_sum:
            dp[0][nums[0]] = 1

    for i in range(1, len(dp)):
        for required_sum in range(0, len(dp[0])):
            sum1 = 0
            if nums[i] <= required_sum:
                sum1 = dp[i-1][required_sum - nums[i]]
            sum2 = dp[i-1][required_sum]
            dp[i][required_sum] = sum1 + sum2
    return dp[len(nums)-1][target_sum]
```
