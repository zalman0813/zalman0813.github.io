---
title: "134. Gas Station"
date: 2023-02-26T21:59:51+08:00
draft: false
tags: ["greedy", "medium"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/gas-station/

Solution: greedy 

```python

# Time Complexity: O(n)
# Space Complexity: O(1)

class Solution:
    def canCompleteCircuit(self, gas: List[int], cost: List[int]) -> int:
        
        if sum(gas) < sum(cost):
            return -1
        start = 0
        total = 0
        
        for i in range(len(gas)):
            total += gas[i] - cost[i]
            
            if total < 0:
                start = i + 1
                total = 0
        return start
```


