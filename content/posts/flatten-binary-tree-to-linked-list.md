---
title: "114. Flatten Binary Tree to Linked List"
date: 2023-04-16T21:10:04+08:00
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

class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right
class Solution:
    head = None
    def flatten(self, root: Optional[TreeNode]) -> None:
        """
        Do not return anything, modify root in-place instead.
        """

        def dfs(root):
            if root.right:
                dfs(root.right)
            if root.left:
                dfs(root.left)
            
            root.left, root.right, self.head = None, self.head, root
        if root:
            dfs(root)
        return root

```
