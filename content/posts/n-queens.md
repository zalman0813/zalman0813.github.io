---
title: "51. N Queens"
date: 2023-03-05T08:04:05+08:00
draft: false
tags: ["169", "hard", "backtracking"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/n-queens/

Status: done

Solution: backtracking

Code:
```python
#Time Complexity: O(n^2)
#Space Complexity: O(n)

class Solution:
    def mapping(self, n, i):
        pattern = ["."]*n
        pattern[i] = 'Q'
        return "".join(pattern)
    def is_valid_move(self, proposed_row, proposed_col, solution):
        for i in range(proposed_row):
            old_row = i
            old_col = solution[i]
            diagonal_offset = proposed_row - old_row
            if (proposed_col == old_col or
               proposed_col + diagonal_offset == old_col or
               proposed_col - diagonal_offset == old_col):
               return False
        return True
    def backtracking(self, n, row, solution, results):
        if row == n:
            results.append([self.mapping(n,i) for i in solution])
        for col in range(n):
            if self.is_valid_move(row, col, solution):
                solution[row] = col
                self.backtracking(n, row+1, solution, results)

    def solveNQueens(self, n: int) -> List[List[str]]:
        results = []
        solution = [-1]*n
        self.backtracking(n, 0, solution, results)
        return results
```



