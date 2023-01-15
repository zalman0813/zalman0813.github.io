---
title: "437. Path Sum Iii"
date: 2023-01-15T23:19:45+08:00
draft: false
tags: ["dfs", "cached", "mediam"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/path-sum-iii/

Solution:
    DFS
Code:
```python
# Time Complexity: O(n)
# Space Complexity: O(n)

def count_paths(root, S):
  # TODO: Write your code here
  m = {}
  return count_paths_recursive(root, S, m, 0)

def count_paths_recursive(curNode, S, cached, curPathSum):
  if not curNode:
    return 0
  
  curPathSum += curNode.val

  path_count = 0

  if curPathSum == S:
    path_count += 1 
  path_count += cached.get(curPathSum - S, 0)

  cached[curPathSum] = cached.get(curPathSum, 0) + 1

  path_count += count_paths_recursive(curNode.left, S, cached, curPathSum)
  path_count += count_paths_recursive(curNode.right, S, cached, curPathSum)

  # Removing the current path sum from the map for backtracking.
  cached[curPathSum] = cached.get(curPathSum, 1) - 1

  return  path_count
```
