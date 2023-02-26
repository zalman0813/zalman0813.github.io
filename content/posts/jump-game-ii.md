---
title: "45. Jump Game Ii"
date: 2023-02-26T21:38:00+08:00
draft: false
tags: ["greedy", "two pointers", "medium"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/jump-game-ii/description/

Solution: greedy 

```python

# Time Complexity: O(n)
# Space Complexity: O(1)

class Solution:
    def jump(self, nums: List[int]) -> int:
        l = r = 0
        times = 0

        while r < len(nums) - 1:
            farthest = 0 
            for i in range(l, r + 1):
                farthest = max(farthest, i+nums[i])
            l = r + 1
            r = farthest
            times += 1
        return times

```
