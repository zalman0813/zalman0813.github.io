---
title: "528. Random Pick With Weight"
date: 2023-02-19T17:05:57+08:00
draft: false
tags: ["binary search", "medium"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/random-pick-with-weight/

Solution: binary search

```python

# Time Complexity: 
#   1. Construct: O(n)
#   2. pickIndex: o(logn)
# Space Complexity: 
#   1. Construct: O(n)
#   2. pickIndex: O(1)
class Solution:

    def __init__(self, w: List[int]):
        self.cum_sums = []
        cum = 0
        for i in range(len(w)):
            cum += w[i]
            self.cum_sums.append(cum)

    def pickIndex(self) -> int:
        target = random.randint(1, self.cum_sums[-1])

        # Assigning low pointer at the start of the array
        low = 0
        # Assigning high pointer at the end of the array
        high = len(self.cum_sums)
        # Binary search to find the target
        while low < high:
            mid = low + (high - low) // 2
            if target > self.cum_sums[mid]:
                low = mid + 1
            else:
                high = mid
        return low

# Your Solution object will be instantiated and called as such:
# obj = Solution(w)
# param_1 = obj.pickIndex()
```


