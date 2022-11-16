---
title: "232. Implement Queue using Stacks"
date: 2022-11-16T23:32:10+08:00
draft: false
tags: ["stack", "169", "easy", "queue"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/implement-queue-using-stacks/

Solution: stack

Code:
two stack

```python
# Time Complexity: O(1)
# Space Complexity: O(n)
class MyQueue:

    def __init__(self):
        self.inStack = []
        self.outStack = []

    def push(self, x: int) -> None:
        self.inStack.append(x)
        return self

    def pop(self) -> int:
        self.move()
        return self.outStack.pop()
    
    def peek(self) -> int:
        self.move()
        return self.outStack[-1]

    def empty(self) -> bool:
        return (not self.inStack) and (not self.outStack)
    
    def move(self):
        if not self.outStack:
            while self.inStack:
                self.outStack.append(self.inStack.pop())
```
