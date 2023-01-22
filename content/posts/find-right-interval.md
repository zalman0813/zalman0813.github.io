---
title: "436. Find Right Interval"
date: 2023-01-22T13:12:57+08:00
draft: false
tags: ["two heaps", "hard"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/find-right-interval/


Solution: two heaps

Code:

```python
# Time Complexity: O(nlogn)
# Space Complexity: O(n)

class Solution:
    def findRightInterval(self, intervals: List[List[int]]) -> List[int]:
        n = len(intervals)

        # heaps for finding the maximum start and end
        maxStartHeap, maxEndHeap = [], []

        result = [0 for x in range(n)]
        for endIndex in range(n):
            heappush(maxStartHeap, (-intervals[endIndex][0], endIndex))
            heappush(maxEndHeap, (-intervals[endIndex][1], endIndex))

        # go through all the intervals to find each interval's next interval
        for _ in range(n):
            # let's find the next interval of the interval which has the highest 'end'
            topEnd, endIndex = heappop(maxEndHeap)
            result[endIndex] = -1  # defaults to - 1
            if -maxStartHeap[0][0] >= -topEnd:
                topStart, startIndex = heappop(maxStartHeap)
                # find the the interval that has the closest 'start'
                while maxStartHeap and -maxStartHeap[0][0] >= -topEnd:
                    topStart, startIndex = heappop(maxStartHeap)
                result[endIndex] = startIndex
                # put the interval back as it could be the next interval of other intervals
                heappush(maxStartHeap, (topStart, startIndex))

        return result
        
```

