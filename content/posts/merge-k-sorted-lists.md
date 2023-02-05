---
title: "23. Merge K Sorted Lists"
date: 2023-02-05T23:13:17+08:00
draft: false
tags: ["K-way merge", " hard", "linked-list"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/kth-smallest-element-in-a-sorted-matrix/description/

Solution: K-way merge

Code:
K-way merge

```python

# Time Complexity: O(nlogk), where k is the number of lists and n is the max length of a single list
# Space Complexity: O(1)

# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def merge_2_lists(self, head1, head2):
        dummy = ListNode(-1)
        prev = dummy  # set prev pointer to dummy node

        # traverse over the lists until both or one of them becomes null
        while head1 and head2:
            if head1.val <= head2.val:
                # if l1 value is <=  l2 value, add l1 node to the list
                prev.next = head1
                head1 = head1.next
            else:
                # if l1 value is greater than l2 value, add l2 node to the list
                prev.next = head2
                head2 = head2.next
            prev = prev.next

        if head1 is not None:
            prev.next = head1
        else:
            prev.next = head2

        return dummy.next
    


    def mergeKLists(self, lists: List[Optional[ListNode]]) -> Optional[ListNode]:
        if len(lists) > 0:
            step = 1
            while step < len(lists):
                for i in range(0, len(lists) - step, step * 2):
                    lists[i] = self.merge_2_lists(lists[i], lists[i + step])
                step *= 2
            return lists[0]
        return None

```


