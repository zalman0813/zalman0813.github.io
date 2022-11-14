---
title: "Balanced Binary Tree"
date: 2022-11-14T19:06:27+08:00
draft: false
tags: ["dfs", "169", "easy", "tree"]
series: ["leetcode"]
categories: ["coding"]
---

Solution: dfs

Code:
```python
def isBalanced(self, root: Optional[TreeNode]) -> bool:
        # use dfs to dive and conquer to find [balanced, height] for each child node.
        def dfs(root):
            if not root:
                return [True, 0]
            
            left, right = dfs(root.left), dfs(root.right)
            
            balanced = left[0] and right[0] and abs(left[1] - right[1]) <= 1
            
            return [ balanced, 1 + max(left[1], right[1])]
                
            
            
        return dfs(root)[0]
```

Time Complexity: O(n)

Space Complexity: O(n)

