---
title: "457. Circular Array Loop"
date: 2023-01-08T17:27:02+08:00
draft: false
tags: ["linked list", "slow fast", "medium"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/rotate-list

Solution:
    slow-fast
Code:
in-place reverse
```python
# Time Complexity: O(n)
# Space Complexity: O(n)

class Solution:
    def circularArrayLoop(self, arr: List[int]) -> bool:

        #remember all the numbers that have been visited
        visited = set()
        for i in range(len(arr)):
            if i in visited:
                continue
            is_forward = arr[i] >= 0  # if we are moving forward or not
            slow, fast = i, i

            # if slow or fast becomes '-1' this means we can't find cycle for this number
            while True:
                # move one step for slow pointer
                slow = self.find_next_index(arr, is_forward, slow)
                # move one step for fast pointer
                fast = self.find_next_index(arr, is_forward, fast)
                if (fast != -1):
                    # move another step for fast pointer
                    fast = self.find_next_index(arr, is_forward, fast)
                if slow == -1 or fast == -1 or slow == fast:
                    break
                visited.add(slow)
                visited.add(fast)

            if slow != -1 and slow == fast:
                return True

        return False


    def find_next_index(self, arr, is_forward, current_index):
        direction = arr[current_index] >= 0

        if is_forward != direction:
            return -1  # change in direction, return -1

        next_index = (current_index + arr[current_index]) % len(arr)

        # one element cycle, return -1
        if next_index == current_index:
            next_index = -1

        return next_index
        
```


