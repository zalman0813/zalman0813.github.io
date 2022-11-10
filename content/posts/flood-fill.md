---
title: "733. Flood Fill"
date: 2022-11-10T20:42:59+08:00
tags: ["dfs", "matrix", "169", "easy"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/flood-fill/

Solution: dfs

Code:
```python
class Solution:
    def floodFill(self, image: List[List[int]], sr: int, sc: int, color: int) -> List[List[int]]:
        
        if image[sr][sc] == color: return image

        # keep original color to compare later
        orgColor = image[sr][sc]
        self.fill(image, sr, sc, orgColor, color)
        return image
    
    def fill(self, image, sr, sc, orgColor, color):
        # 1. skip if over matrix range
        # 2. skip if the color is not the same
        if (
            sr < 0 or sc < 0 or
            sr >= len(image) or sc >= len(image[0])
         or image[sr][sc] != orgColor):
            return
        
        # change the color, and then 
        image[sr][sc] = color
        directions = [[1,0],[0,1],[-1,0], [0,-1]]
        for dr, dc in directions:
            self.fill(image, sr+dr, sc+dc, orgColor, color)
```

Time Complexity: O(m*n)
Space Complexity: O(m*n)
