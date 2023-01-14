---
title: "199. Binary Tree Right Side View"
date: 2023-01-14T22:24:32+08:00
draft: false
tags: ["binary tree", "bfs", "medium"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/binary-tree-maximum-path-sum

Solution:
    dfs
Code:
```python
# Time Complexity: O(n)
# Space Complexity: O(n)

# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
from collections import deque
class Solution:
    def rightSideView(self, root: Optional[TreeNode]) -> List[int]:
        if not root:
            return []
        result = []
        q = deque()

        q.append(root)

        while q:
            for i in range(len(q)):
                curNode = q.popleft()
                if curNode.left:
                    q.append(curNode.left)
                if curNode.right:
                    q.append(curNode.right)
            result.append(curNode.val)
        return result

        
```
