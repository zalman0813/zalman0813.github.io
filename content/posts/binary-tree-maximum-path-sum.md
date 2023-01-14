---
title: "124. Binary Tree Maximum Path Sum"
date: 2023-01-14T22:10:29+08:00
draft: false
tags: ["binary tree", "dfs", "hard"]
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
class Solution:

    def maxPathSum(self, root: Optional[TreeNode]) -> int:

        self.globalPathSum = -math.inf
        self.pathRecursive(root)
        return self.maxDiameter

    def pathRecursive(self, curNode):
        if not curNode:
            return 0

        maxPathSumFromLeftNode = self.pathRecursive(curNode.left)
        maxPathSumFromRightNode = self.pathRecursive(curNode.right)

        # ignore paths with negative sums, since we need to find thhe maximum sum we should
        # ignore any path which has an overall negative sum.
        maxPathSumFromLeftNode = max(maxPathSumFromLeftNode, 0)
        maxPathSumFromRightNode = max(maxPathSumFromRightNode, 0)

        pathSum =  maxPathSumFromLeftNode + maxPathSumFromRightNode + curNode.val
        self.globalPathSum = max(self.globalPathSum, pathSum)

        return max(maxPathSumFromLeftNode, maxPathSumFromRightNode) + curNode.val


        
```




