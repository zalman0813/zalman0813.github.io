---
title: "Merge Two Sorted Lists"
date: 2022-11-02T22:05:02+08:00
draft: false
---

Link: https://leetcode.com/problems/merge-two-sorted-lists/

Tags: two pointer, 169, liniked list

Status: done

Solution: two pointer

Code:
```python
class Solution:
    def mergeTwoLists(self, list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:

        dummy = ListNode()
        tail = dummy
        
        
        while list1 and list2:
            if list1.val > list2.val:
                tail.next = list2
                list2 = list2.next
            else:
                tail.next = list1
                list1 = list1.next
            tail = tail.next
        
        if list1:
            tail.next = list1
        if list2:
            tail.next = list2
            
        return dummy.next
```

Time Complexity: O(n)

Space Complexity: O(1)