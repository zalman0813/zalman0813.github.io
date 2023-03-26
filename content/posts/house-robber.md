---
title: "198. House Robber"
date: 2023-03-26T09:19:39+08:00
draft: false
tags: ["medium", "dp", "recursive numbers"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/fibonacci-number

Status: done

Solution: dp-bottom up

Code:
```python
#Time Complexity: O(n)
#Space Complexity: O(1)
class Solution:
    def rob(self, nums: List[int]) -> int:
        
        rob1, rob2 = 0, 0
        
        #[rob1, rob2, n, n+1, ...]
        for n in nums:
            temp = max(n + rob1, rob2)
            rob1 = rob2
            rob2 = temp
        return rob2
```

```python
#Time Complexity: O(n)
#Space Complexity: O(1)
class Solution:
    def rob(self, nums: List[int]) -> int:
        
        rob1, rob2 = 0, 0
        
        #[rob1, rob2, n, n+1, ...]
        for n in nums:
            temp = max(n + rob1, rob2)
            rob1 = rob2
            rob2 = temp
        return rob2
```

```python
# top-down by recursive, which will be timeout
#Time Complexity: O(n)
#Space Complexity: O(n)
class Solution:
    def rob(self, nums: List[int]) -> int:
        
        dp = [0]*len(nums)
        def helper(i, nums, dp):
            if i >= len(nums):
                return 0
            if dp[i] == 0:
                rob = helper(i+2, nums, dp) + nums[i]
                not_rob = helper(i+1, nums, dp)
                dp[i] = max(rob, not_rob)
            return dp[i]
        return helper(0, nums, dp)
```

