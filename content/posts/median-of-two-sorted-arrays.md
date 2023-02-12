---
title: "4. Median of Two Sorted Arrays"
date: 2023-02-12T11:16:44+08:00
draft: false
tags: ["k-ways merge", "binary search","hard"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/median-of-two-sorted-arrays/

Solution: k-ways merge

Code:
```python
# Time Complexity: O(log(min(m,n)))
# Space Complexity: O(1)
class Solution:
    def findMedianSortedArrays(self, nums1: List[int], nums2: List[int]) -> float:
        
        if len(nums1) > len(nums2):
            return self.findMedianSortedArrays(nums2, nums1)
        
        if len(nums1) == 0:
            if len(nums2) % 2 == 0:
                return (nums2[len(nums2)//2 - 1] + nums2[len(nums2)//2])/2
            else:
                return nums2[len(nums2)//2]
        tot_len = len(nums1) + len(nums2)
        start, end = 0, len(nums1)
        while start <= end:
            cut_1 = (start + end) // 2
            cut_2 = (tot_len + 1) // 2 - cut_1

            left_1 = float(-inf) if cut_1 == 0 else nums1[cut_1 - 1]
            right_1 = float(inf) if cut_1 == len(nums1) else nums1[cut_1]

            left_2 =  float(-inf) if cut_2 == 0 else nums2[cut_2 - 1]
            right_2 = float(inf) if cut_2 == len(nums2) else nums2[cut_2]

            if left_1 > right_2:
                end = cut_1 - 1
            elif left_2 > right_1:
                start = cut_1 + 1
            else:
                if tot_len % 2 == 0:
                    return (max(left_1, left_2) + min(right_1, right_2)) / 2
                else:
                    return max(left_1, left_2)
        return -1

```

