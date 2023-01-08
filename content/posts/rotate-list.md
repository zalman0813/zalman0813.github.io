---
title: "61. Rotate List"
date: 2023-01-08T16:44:33+08:00
draft: false
tags: ["linked list", "in-place reverse", "medium"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/rotate-list

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
    def rotateRight(self, head: Optional[ListNode], k: int) -> Optional[ListNode]:
        if k <= 0 or not head:
            return head
        # find last node and length
        last_node = head
        list_length = 1
        while last_node.next:
            last_node = last_node.next
            list_length += 1 
        # connect the last node with the head to make it a circular list
        last_node.next = head

        # no need to do rotations more than the length of the list
        k %= list_length
        skip_length = list_length - k

        last_node_of_rotated_list = head
        for _ in range(skip_length - 1):
            last_node_of_rotated_list = last_node_of_rotated_list.next
        head = last_node_of_rotated_list.next
        last_node_of_rotated_list.next = None
        return head
        
```

