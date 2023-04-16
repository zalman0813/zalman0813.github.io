---
title: "1466. Reorder Routes to Make All Paths Lead to the City Zero"
date: 2023-04-16T18:40:15+08:00
draft: false
tags: ["dfs"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/reorder-routes-to-make-all-paths-lead-to-the-city-zero

Solution: dfs

Code:
```python
# Time Complexity: O(n).
# Space Complexity: O(n). 
class Solution:
    def minReorder(self, n: int, connections: List[List[int]]) -> int:

        visited = set()
        edges = { (a, b) for a, b in connections }
        neighbor = { city: [] for city in range(n) }
        changes = 0

        for a, b in connections:
            neighbor[a].append(b)
            neighbor[b].append(a)

        def dfs(city):
            nonlocal visited, edges, neighbor, changes

            for c in neighbor[city]:
                if c in visited:
                    continue
                if (c, city) not in edges:
                    changes += 1
                visited.add(c)
                dfs(c)
        visited.add(0)
        dfs(0)
        return changes
```

