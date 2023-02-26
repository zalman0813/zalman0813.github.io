---
title: "1029. Two City Scheduling"
date: 2023-02-26T21:56:28+08:00
draft: false
tags: ["greedy", "sorted","medium"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/two-city-scheduling/

Solution: greedy 

```python

# Time Complexity: O(nlogn)
# Space Complexity: O(m + n), m represents the memory required to sort this array.
# Python uses a combination of merge sort and insertion sort which can sort the array in O(m)

class Solution:
    def twoCitySchedCost(self, costs: List[List[int]]) -> int:

        diff = []

        for costa, costb in costs:
            diff.append([costa - costb, costa, costb])
        
        diff.sort()

        result = 0
        tot = len(costs)
        for i in range(tot):
            if i >= tot / 2:
                result += diff[i][2]
            else:
                result += diff[i][1]
        return result 

```
