---
title: "206. Reverse Linked List"
date: 2022-11-23T23:58:22+08:00
draft: false
tags: ["linked list", "169", "easy"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/reverse-linked-list/

Solution:
    linked-list

Code:
 linked-list
```python
# Time Complexity: O(n)
# Space Complexity: O(1)
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        hashMap = {}
        
        for i, num in enumerate(nums):
            rest = target - num
            if rest in hashMap:
                return [i, hashMap[rest] ]
            hashMap[num] = i
```



