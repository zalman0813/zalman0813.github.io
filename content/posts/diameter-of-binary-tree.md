---
title: "543. Diameter of Binary Tree"
date: 2022-12-07T00:00:24+08:00
draft: false
tags: ["dfs", "169", "easy"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/diameter-of-binary-tre


Solution: dfs

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
class Solution:
    def diameterOfBinaryTree(self, root: Optional[TreeNode]) -> int:
        self.max_diameter = 0
        self.getDiameter(root)
        return self.max_diameter
    
    def getDiameter(self, root):
        if not root:
            return 0
        
        left_depth = self.getDiameter(root.left)
        right_depth = self.getDiameter(root.right)
        # get the diameter between two nodes
        diameter = left_depth + right_depth
        
        # get the maximum diameter
        self.max_diameter = max(self.max_diameter, diameter)
        return max(left_depth, right_depth) + 1
        
```





