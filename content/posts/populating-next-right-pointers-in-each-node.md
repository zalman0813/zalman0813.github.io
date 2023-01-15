---
title: "117. Populating Next Right Pointers in Each Node"
date: 2023-01-15T23:38:24+08:00
draft: false
tags: ["bfs", "mediam"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/populating-next-right-pointers-in-each-node

Solution:
    BFS
Code:
```python
# Time Complexity: O(n)
# Space Complexity: O(n)


"""
# Definition for a Node.
class Node:
    def __init__(self, val: int = 0, left: 'Node' = None, right: 'Node' = None, next: 'Node' = None):
        self.val = val
        self.left = left
        self.right = right
        self.next = next
"""

class Solution:
    def connect(self, root: 'Optional[Node]') -> 'Optional[Node]':
        if not root:
            return None
        q = deque()
        q.append(root)
        while q:
            prevNode = None
            for _ in range(len(q)):
                curNode = q.popleft()
                if prevNode:
                    prevNode.next = curNode
                if curNode.left:
                    q.append(curNode.left)
                if curNode.right:
                    q.append(curNode.right)
                prevNode = curNode
                curNode.next = None

        return root
```
