---
title: "1.two Sum"
date: 2022-10-31T22:01:45+08:00
draft: false
tags: ["two pointer", "169", "easy", "hashmap"]
series: ["leetcode"]
categories: ["coding"]
---

Solution:
    HashMap, Two Pointer

Note:
  1. hashmap: dictionay to store key as num, value as index.
  2. tow pointer: sorted and find original index. Need to consider the same value

Code:
1. hashmap
```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        hashMap = {}
        
        for i, num in enumerate(nums):
            rest = target - num
            if rest in hashMap:
                return [i, hashMap[rest] ]
            hashMap[num] = i
```
Time Complexity: O(n)
Space Complexity: O(n)

2. two pointer
```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        l = 0
        r = len(nums) - 1
        if nums[l] + nums[r] == target:
            return [l, r]

        sorted_nums = sorted(nums)        
        while l < r :
            if sorted_nums[l] + sorted_nums[r] == target:
                if sorted_nums[l] == sorted_nums[r]:
                    return [nums.index(sorted_nums[l]), 
                            nums.index(sorted_nums[l],nums.index(sorted_nums[l])+1)]
                else:
                    return [nums.index(sorted_nums[l]), nums.index(sorted_nums[r])]
            if sorted_nums[l] + sorted_nums[r] > target:
                r-=1
            else:
                l+=1
```
Time Complexity: O(nlogn)
Space Complexity: O(n)