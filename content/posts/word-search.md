---
title: "79. Word Search"
date: 2023-03-05T08:06:48+08:00
draft: false
tags: ["169", "medium", "backtracking"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/word-search/

Status: done

Solution: backtracking

Code:
```python
#Time Complexity: O(n×3^l)
#Space Complexity: O(l), , where l is the length of the word to be searched in the grid.

class Solution:
    def word_search(self, grid, word):
        n = len(grid)
        if n < 1:
            return False
        m = len(grid[0])
        if m < 1:
            return False
        for row in range(n):
            for col in range(m):
                if self.depth_first_search(row, col, grid, word):
                    return True
        return False
    def depth_first_search(self,row, col, grid, word):
        if len(word) == 0:
            return True

        if row < 0 or row == len(grid) or col < 0 or col == len(grid[0]) \
                or word[0].lower() != grid[row][col].lower():
            return False
        
        result = False
        grid[row][col] = '*'
        for offset_x, offset_y in [[1,0], [-1,0], [0, 1], [0, -1]]:
            result = self.depth_first_search(row + offset_x, col + offset_y, grid, word[1:])
            if result:
            break
        grid[row][col] = word[0]
        return result

```





