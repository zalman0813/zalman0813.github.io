---
title: "417. Pacific Atlantic Water Flow"
date: 2023-02-05T23:33:04+08:00
draft: false
tags: ["dfs", "169", "medium"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/pacific-atlantic-water-flow/

Solution: dfs

Code: dfs

```python

# Time Complexity: O(m*n)
# Space Complexity: O(m*n)
class Solution:
    def pacificAtlantic(self, heights: List[List[int]]) -> List[List[int]]:
        
        pac = set()
        atl = set()
        
        ROWS = len(heights)
        COLS = len(heights[0])
        
        def dfs(r, c, visit, prevHeight):
            
            if ((r, c) in visit or
                r < 0 or c < 0 or r >= ROWS or c >= COLS or
                 heights[r][c] < prevHeight
               ):
                return
            visit.add((r,c))
            
            dfs(r + 1, c, visit, heights[r][c])
            dfs(r - 1, c, visit, heights[r][c])
            dfs(r, c + 1, visit, heights[r][c])
            dfs(r, c - 1, visit, heights[r][c])
            
        
        for c in range(COLS):
            dfs(0, c, pac, heights[0][c])
            dfs(ROWS - 1, c, atl, heights[ROWS - 1][c])
        
        for r in range(ROWS):
            dfs(r, 0, pac, heights[r][0])
            dfs(r, COLS - 1, atl, heights[r][COLS-1])
        
        res = []
        for r in range(ROWS):
            for c in range(COLS):
                if (r, c) in pac and (r, c) in atl:
                    res.append([r,c])
        return res

```

