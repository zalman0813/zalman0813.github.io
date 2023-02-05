---
title: "1730. Shortest Path to Get Food"
date: 2023-02-05T23:28:13+08:00
draft: false
tags: ["bfs", "169", "medium"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/shortest-path-to-get-food/

Solution: bfs

Code:
bfs

```python

# Time Complexity: O(m*n)
# Space Complexity: O(m*n)
class Solution:
	def getFood(self, grid):
		ROWS, COLS = len(grid), len(grid[0])
		visit, queue = set(), collections.deque()
		for r in range(ROWS):
			for c in range(COLS):
				if grid[r][c] == '*':
					queue.append((r,c, 0))
					visit.add((r,c))
					break
		directions = [(1,0),(0,-1), (-1,0), (0,1)]
		while queue:
			cur_r, cur_c, steps = queue.popleft()
			if grid[cur_r][cur_c] == '#':
					return steps
			else:
				for dr,dc in directions:
					new_r, new_c = r + dr, c + dc
					if (0<=new_r<ROWS) and (0<=new_c<COLS) and grid[new_r][new_c] != 'X' and (new_r, new_c) not in visit:
					
					queue.append((new_r, new_c, steps+1))
					visit.add(new_r, new_c)
				
		return -1

```

