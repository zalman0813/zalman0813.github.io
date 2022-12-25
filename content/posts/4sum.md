---
title: "18. 4sum"
date: 2022-12-25T21:42:19+08:00
draft: false
tags: ["two pointers", "169", "easy"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/4sum

Status: done

Solution: two pointers

Code:
Time Complexity: O(nlogn) + O(n^3) => O(n)

Space Complexity: O(n)

```python
class Solution:
    def fourSum(self, arr: List[int], target: int) -> List[List[int]]:
        quadruplets = []
        # TODO: Write your code here
        arr.sort()
        for i in range(0, len(arr) - 3):
            if i > 0 and arr[i] == arr[i - 1]:
                continue
            for j in range(i + 1, len(arr) - 2):
                if j > i + 1 and arr[j] == arr[j - 1]:
                    continue
                left = j + 1
                right = len(arr) - 1
                while left < right:
                    target_sum = target - arr[i] - arr[j] - arr[left] - arr[right]
                    if target_sum == 0:
                        quadruplets.append([arr[i], arr[j], arr[left], arr[right]])
                        left += 1
                        right -= 1
                        while left < right and arr[left] == arr[left - 1]:
                            left += 1
                        while left < right and arr[right] == arr[right + 1]:
                            right -= 1
                    elif target_sum > 0:
                        left+=1
                    else:
                        right-=1
        return quadruplets
```