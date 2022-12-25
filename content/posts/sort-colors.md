---
title: "75. Sort Colors"
date: 2022-12-25T21:47:51+08:00
draft: false
tags: ["two pointers", "169", "easy"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/sort-colors

Status: done

Solution: two pointers

Code:
Time Complexity: O(n)

Space Complexity: O(1)
```python
class Solution:
    def sortColors(self, arr: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        
        low = 0
        high = len(arr) - 1
        i = 0
        while i <= high:
            if arr[i] == 0:
                arr[i], arr[low] = arr[low], arr[i]
                low += 1
                i += 1
            elif arr[i] == 2:
                arr[i], arr[high] = arr[high], arr[i]
                high -= 1
            else:
                i += 1
            
        return arr
```