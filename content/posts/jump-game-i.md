---
title: "55. Jump Game I"
date: 2023-02-26T22:00:30+08:00
draft: false
tags: ["greedy", "medium"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/jump-game/

Solution: greedy 

```python

# Time Complexity: O(n)
# Space Complexity: O(1)

class Solution:
    def canJump(self, nums: List[int]) -> bool:
        end = len(nums) - 1
        for i in range(len(nums) - 2, -1, -1):
            if i + nums[i] >= end:
                end = i
        if end == 0:
            return True
        return False
```


