---
title: "92. Reverse Linked List Ii"
date: 2023-01-08T14:29:47+08:00
tags: ["in-place reversal", "medium"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/reverse-linked-list-ii

Solution: in-place reversal of a linkedlist

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
    def reverseBetween(self, head: Optional[ListNode], left: int, right: int) -> Optional[ListNode]:
 
        if left == right:
            return head
        # after skipping 'left-1' nodes, current will point to 'left'th node
        prev, cur = None, head
        i = 0
        while cur and i < left - 1:
            prev, cur = cur, cur.next
            i += 1
        
        # we are intersted in three parts of the LinkedList, the part before index 'left', the part between 'left' and 'right', and the part after index 'right'      
        last_node_of_first_part = prev
        last_node_of_sub_list = cur

        # reverse sublist between left and right
        i = 0             
        while cur and i < right - left + 1:
            temp = cur.next
            cur.next = prev
            prev = cur
            cur = temp
            i += 1

        # connect with the first part
        if last_node_of_first_part is not None:
            # previous is now the first node of the sub-list
            last_node_of_first_part.next = prev
        # this means left == 1 we are changing the first node (head) of the linkedlist
        else:
            head = prev
        # connect with the last part
        last_node_of_sub_list.next = cur
        return head
```
