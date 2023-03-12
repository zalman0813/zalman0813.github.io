---
title: "416. Partition Equal Subset Sum"
date: 2023-03-12T21:58:49+08:00
draft: false
tags: ["medium", "dp"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/partition-equal-subset-sum/

Status: done

Solution: dp-bottom up

Code:
```python
#Time Complexity: O(n*m), where m = sum(nums)
#Space Complexity: O(n)
class Solution:
    def canPartition(self, nums: List[int]) -> bool:
        if sum(nums) % 2 != 0:
            return False
        target = sum(nums) // 2
        
        dp = set()
        dp.add(0)  
        for i in range(len(nums)-1, -1, -1):
            nextDp = set()
            for t in dp:
                if t + nums[i] == target:
                    return True
                nextDp.add(t+nums[i])
                nextDp.add(t)
            dp = nextDp
        
        return False

```

