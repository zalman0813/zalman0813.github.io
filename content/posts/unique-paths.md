---
title: "Unique Paths"
date: 2023-03-25T18:24:21+08:00
draft: false
tags: ["medium", "dp", "recursive numbers"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/fibonacci-number

Status: done

Solution: dp-bottom up

Code:
```python
#Time Complexity: O(m*n)
#Space Complexity: O(m)
class Solution:
    
    def uniquePaths(self, m: int, n: int) -> int:
        col = [1]*m
        
        for i in range(n-1):
            newCol = [1]*m
            for j in range(m - 2, -1, -1):
                newCol[j] = newCol[j+1] + col[j]
            col = newCol
        return col[0]
```

