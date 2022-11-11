---
title: "235. Lowest Common Ancestor of a Binary Search Tree"
date: 2022-11-11T23:20:24+08:00
draft: false
tags: ["dfs", "169", "medium", "binay search", "recursive"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/

Status: done

Solution: binary search, dfs, recursive

Code:
1. binary search
```python
# Time Complexity: O(LogN)
# Space Complexity: O(1)
class Solution:
    def lowestCommonAncestor(self, root: 'TreeNode', p: 'TreeNode', q: 'TreeNode') -> 'TreeNode':
        
        cur = root 
        
        while cur:
            if cur.val > p.val and cur.val > q.val:
                cur = cur.left
            elif cur.val < p.val and cur.val < q.val:
                cur = cur.right
            else:
                return cur
```

2. dfs - without binary search info - "236. Lowest Common Ancestor of a Binary Tree"
```python
# Time Complexity: O(LogN)
# Space Complexity: O(LogN)
class Solution:
    def lowestCommonAncestor(self, root: 'TreeNode', p: 'TreeNode', q: 'TreeNode') -> 'TreeNode':
        
        if root == p or root == q or not root:
            return root
        
        left = self.lowestCommonAncestor(root.left, p, q)
        right = self.lowestCommonAncestor(root.right, p, q)
        
        if left and right:
            return root
        elif left:
            return left
        elif right:
            return right
```



3. dfs - with binary search info
```python
# Time Complexity: O(LogN)
# Space Complexity: O(LogN)
class Solution:
    def lowestCommonAncestor(self, root: 'TreeNode', p: 'TreeNode', q: 'TreeNode') -> 'TreeNode':
    
        if root.val > p.val and root.val > q.val:
            return self.lowestCommonAncestor(root.left, p, q)
        elif root.val < p.val and root.val < q.val:
            return self.lowestCommonAncestor(root.right, p, q)
        else:
            return root
```