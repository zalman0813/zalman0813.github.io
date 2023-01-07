---
title: "42. First Missing Positive"
date: 2023-01-07T21:57:48+08:00
draft: false
tags: ["cyclic sort", "hard"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/first-missing-positive

Solution: cyclic sort

Code:
```python
# Time Complexity: O(n)
# Space Complexity: O(1)

class Solution:
    def firstMissingPositive(self, nums: List[int]) -> int:
        i = 0
        n = len(nums)

        while i < n:
            j = nums[i] - 1
            if nums[i] > 0 and nums[i] <= n and nums[i] != nums[j]:
                nums[i], nums[j] = nums[j], nums[i]
            else:
                i += 1
        for i in range(n):
            if nums[i] != i + 1:
                return i + 1
        # if missing number is over n, it's as n + 1
        return n + 1
```




