---
title: "6297. Sort the Students by Their Kth Score"
date: 2023-01-22T11:25:42+08:00
tags: ["contest", "easy", "heap"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/contest/weekly-contest-329/problems/sort-the-students-by-their-kth-score/

Code:
```python
# Time Complexity: O(nlogn)
# Space Complexity: O(n)
from heapq import *
class Solution:
    def sortTheStudents(self, score: List[List[int]], k: int) -> List[List[int]]:
        maxHeap = []
        
        for i in range (len(score)):
            heappush(maxHeap, (-score[i][k], i))
        
        result = []
        
        while maxHeap:
            student_score, i = heappop(maxHeap)
            result.append(score[i])
        return result
```
