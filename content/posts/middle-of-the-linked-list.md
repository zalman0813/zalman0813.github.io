---
title: "876. Middle of the Linked List"
date: 2022-12-07T22:27:27+08:00
draft: false
tags: ["two pointer", "169", "easy"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/middle-of-the-linked-list/

Status: done

Solution: two pointer

Code:
```python
# Time Complexity: O(n)
# Space Complexity: O(1)

# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def middleNode(self, head: Optional[ListNode]) -> Optional[ListNode]:
        
        low = fast = head

        while fast and fast.next:
            low = low.next
            fast = fast.next.next
        
        return low
```





