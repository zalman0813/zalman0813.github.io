---
title: "881. Boats to Save People"
date: 2023-02-26T22:00:13+08:00
draft: false
tags: ["greedy", "sorted","medium"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/boats-to-save-people/description/

Solution: greedy 

```python

# Time Complexity: O(nlogn)
# Space Complexity: O(n), n represents the memory required to sort this array.

class Solution:
    def numRescueBoats(self, people: List[int], limit: int) -> int:
        people.sort()
        
        l = 0
        r = len(people) - 1

        boats = 0
        while l <= r:
            if people[l] + people[r] <= limit:
                l += 1
            r -= 1
            boats += 1
        return boats
```


