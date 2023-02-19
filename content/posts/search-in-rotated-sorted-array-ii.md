---
title: "81. Search in Rotated Sorted Array Ii"
date: 2023-02-19T17:43:27+08:00
draft: false
tags: ["binary search", "medium"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/search-in-rotated-sorted-array-ii

Solution: binary search

```python

# Time Complexity: O(log(n))
# Space Complexity: O(1)
class Solution:
    def search(self, nums: List[int], target: int) -> bool:

        if len(nums) == 1:
            if nums[0] == target:
                return True
            else:
                return False

        l, r = 0, len(nums) - 1        
       
        while l <= r:
            # shifting to remove duplicate elements
            while l<r and nums[l] == nums[l+1]:
                l+=1
            while l<r and nums[r] == nums[r-1]:
                r-=1
            mid = (l + r) // 2 
            if target == nums[mid]:
                return True
            
            if nums[l] <= nums[mid]:
                if target >= nums[l] and target < nums[mid]:
                    r = mid - 1
                else:
                    l = mid + 1
            else:
                if target > nums[mid] and target <= nums[r]:
                    l = mid + 1
                else:
                    r = mid - 1
        return False

```

