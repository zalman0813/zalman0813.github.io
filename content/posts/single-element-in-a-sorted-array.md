---
title: "540. Single Element in a Sorted Array"
date: 2023-02-19T17:17:20+08:00
draft: false
tags: ["binary search", "medium"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/single-element-in-a-sorted-array/

Solution: binary search

```python

# Time Complexity: O(log(n))
# Space Complexity: O(1)
class Solution:
    def singleNonDuplicate(self, nums: List[int]) -> int:
        l, r = 0, len(nums) - 1

        while l < r:
            m = l + (r-l)//2

            # use the pair arrangement propert. even is equalt to next odd until an unpaired number appears,
            # If the element at mid and mid + 1 are the same then
            # the single element must appear after the mid point
            # Otherwise we must search before the mid point

            if m % 2 == 1:
                m -= 1 # to preceding even index
            
            if nums[m] == nums[m + 1]:
                l = m + 2
            else:
                r = m
        return nums[l]
```


