---
title: "Partition a Set Into Two Subsets Such That the Difference of Subset Sums Is Minimum"
date: 2023-03-19T22:11:16+08:00
draft: false
tags: ["hard", "dp"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://www.codingninjas.com/codestudio/problems/partition-a-set-into-two-subsets-such-that-the-difference-of-subset-sums-is-minimum_842494?leftPanelTab=0

Status: done

Solution: dp-top down

Code:
```python
#Time Complexity: O(n*s), where s is the target sum
#Space Complexity: O(n*s)
def minSubsetSumDifference(nums, n):
    # Write your code here.
    # Return the minimum difference in the form of an integer.
    dp = [[-1 for _ in range(sum(nums)+1)] for i in range(len(nums))]
    return rec(nums,0,  0, 0, dp)



def rec(nums, i, sum1, sum2, dp):
    if i == len(nums):
        return abs(sum1 - sum2)

    if dp[i][sum1] == -1:

        dp[i][sum1] = min(
            rec(
                nums, i + 1, sum1 + nums[i], sum2, dp
            ),
            rec(
                nums, i + 1, sum1, sum2 + nums[i], dp
            ),
        )
    return dp[i][sum1]
```