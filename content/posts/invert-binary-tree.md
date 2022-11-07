---
title: "Invert Binary Tree"
date: 2022-11-07T22:48:58+08:00
draft: false
tags: ["dfs", "169", "easy"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/invert-binary-tree/

Solution: dfs

Code:
```python
class Solution:
    def invertTree(self, root: Optional[TreeNode]) -> Optional[TreeNode]:
        if not root:
            return None

        root.left, root.right = root.right, root.left
        
        self.invertTree(root.left)
        self.invertTree(root.right)
        return root
```

Time Complexity: O(n)

Space Complexity: O(n)