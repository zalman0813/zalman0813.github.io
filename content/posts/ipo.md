---
title: "502. Ipo"
date: 2023-01-21T16:44:56+08:00
draft: false
tags: ["hard", "two heaps"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/ipo/

Solution: two heaps

Code:
two heaps

```python
# Time Complexity: O(nlogn + klogn) , n is the total number of projects, k is the total number of projects we are selecting
# Space Complexity: O(n)
from heapq import *
class Solution:
    def findMaximizedCapital(self, k: int, w: int, profits: List[int], capital: List[int]) -> int:

        minCapitalHeap = []
        maxProfitHeap = []

        # add all projects into minHeap, so that we can select a project with the smallest capital requirement. 
        for i in range(len(capital)):
            heappush(minCapitalHeap, (capital[i], i))
        
        # let's try to find a total of 'k' best projects
        availableCapital = w
        for _ in range(k):

            # find all project that can be selected within the available capital and insert them in a max-heap
            while minCapitalHeap and minCapitalHeap[0][0] <= availableCapital:
                capital, i = heappop(minCapitalHeap)
                heappush(maxProfitHeap, (-profits[i], i))
            
            if not maxProfitHeap:
                break
            # select the project with the maximum profit
            availableCapital += -heappop(maxProfitHeap)[0]

        return availableCapital

```

