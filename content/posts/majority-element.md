---
title: "169. Majority Element"
date: 2022-11-24T19:39:00+08:00
draft: false
tags: ["sorted", "169", "easy", "counting"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/majority-element/

Status: done

Solution: sorted, counting

Code:
1. sorted
```python
# Time Complexity: O(nlogn)
# Space Complexity: O(1)
class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        nums.sort()
        # majority element that appears more than ⌊n / 2⌋ times, so mid will be the majority element.
        mid = len(nums) // 2
        return nums[mid]
```
2. counting
```python
# Time Complexity: O(n)
# Space Complexity: O(1)
class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        res, counts = 0, 0

        for n in nums:
            # When counts == 0, we initate res.
            # Because the majority is more than (n/2),  the majority will be the final res.
            if counts == 0:
                res = n
            counts += (1 if res == n else -1) 
        return res
```



