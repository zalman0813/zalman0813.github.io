---
title: "141. Linked List Cycle"
date: 2022-11-15T22:16:09+08:00
draft: false
tags: ["fast & slow pointer", "169", "easy", "liniked list"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/linked-list-cycle/

Status: done

Solution: Fast & Slow Pointer

Code:
```python
class Solution:
    def hasCycle(self, head: Optional[ListNode]) -> bool:
        slow, fast = head, head
        
        while fast and fast.next:
            slow = slow.next
            fast = fast.next.next
            
            if slow == fast:
                return True

        return False
```

Time Complexity: O(n)

Space Complexity: O(1)
