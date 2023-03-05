---
title: "337. House Robber Iii"
date: 2023-03-05T08:20:19+08:00
draft: false
tags: ["169", "medium", "backtracking"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/house-robber-iii/

Status: done

Solution: backtracking

Code:
```python
#Time Complexity: O(n)
#Space Complexity: O(h), , where h is the height of the tree

# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def dfs(self, root):
        if root is None:
            return [0, 0]
        leftChild = self.dfs(root.left)
        rightChild = self.dfs(root.right)

        not_node = max(leftChild) + max(rightChild)
        node = root.val + leftChild[1] + rightChild[1]
        return [node, not_node]

    def rob(self, root: Optional[TreeNode]) -> int:
        return max(self.dfs(root))

```

