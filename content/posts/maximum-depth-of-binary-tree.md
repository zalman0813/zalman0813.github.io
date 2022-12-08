---
title: "104. Maximum Depth of Binary Tree"
date: 2022-12-08T22:32:48+08:00
draft: false
tags: ["dfs", "169", "easy"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/maximum-depth-of-binary-tree

Status: done

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
    def maxDepth(self, root: Optional[TreeNode]) -> int:
        return self.get_depth(root)
    
    def get_depth(self, root):
        if not root:
            return 0
        left_depth = self.get_depth(root.left)
        right_depth = self.get_depth(root.right)
        return 1 + max(left_depth, right_depth)
```







