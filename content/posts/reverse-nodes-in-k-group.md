---
title: "25. Reverse Nodes in K Group"
date: 2023-01-08T15:28:49+08:00
draft: false
tags: ["linked list", "in-place reverse", "hard"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/reverse-nodes-in-k-group

Solution:
    linked-list

Code:
in-place reverse
```python
# Time Complexity: O(n)
# Space Complexity: O(1)

# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def reverseKGroup(self, head: Optional[ListNode], k: int) -> Optional[ListNode]:
        if k <= 1 or head is None:
            return head

        prev, cur = None, head
        
        while cur:
            last_node_of_last_part, last_node_of_cur_group = prev, cur
            #check if rest of nodes is less than k.
            tail = cur
            for i in range(k):
                if tail is None:
                    return head
                tail = tail.next

            i = 0
            
            while cur and i < k:
                tmp = cur.next
                cur.next = prev
                prev = cur
                cur = tmp
                i += 1
            
            #prev is the first node of current group
            #cur is the first node of next part
            if last_node_of_last_part is not None:
                last_node_of_last_part.next = prev
            else:
                head = prev
            last_node_of_cur_group.next = cur
            prev = last_node_of_cur_group
        return head
```

recursive? - https://leetcode.com/problems/reverse-nodes-in-k-group/solutions/11676/64ms-python-solution-1/
```python
# Time Complexity: O(n)
# Space Complexity: O(1)
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def reverseKGroup(self, head: Optional[ListNode], k: int) -> Optional[ListNode]:
        if not head and not head.next:
            return head
        
        tail = head
        for i in range(k):
            if not tail:
                return tail
            tail = tail.next

        tail = self.reverseGroup(tail, k)

        for i in range(k):
            next = head.next
            head.next = tail
            tail = head
            head = next
        return tail
```