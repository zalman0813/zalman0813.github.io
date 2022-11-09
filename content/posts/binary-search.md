---
title: "704. Binary Search"
date: 2022-11-09T21:19:27+08:00
draft: false
tags: ["two pointer", "169", "easy"]
series: ["leetcode"]
categories: ["coding"]
---


Solution: two pointer

Code:
```python
class Solution:
    class Solution:
    def search(self, nums: List[int], target: int) -> int:
        if len(nums) == 1:
            return 0 if nums[0] == target else -1
        
        l = 0
        r = len(nums) - 1
        
        while l <= r:
            mid = (l + r) // 2
            if nums[mid] > target:
                r = mid -1
            elif nums[mid] < target:
                l = mid + 1
            else:
                return mid
        return -1
```

Time Complexity: O(logn)
Space Complexity: O(1)

Link: https://leetcode.com/problems/binary-search/

