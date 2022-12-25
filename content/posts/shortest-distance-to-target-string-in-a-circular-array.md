---
title: "2515. Shortest Distance to Target String in a Circular Array"
date: 2022-12-25T21:53:07+08:00
draft: false
tags: ["two pointers", "169", "easy"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/contest/weekly-contest-325/problems/shortest-distance-to-target-string-in-a-circular-array/

Status: done

Solution: two pointers

Code:
Time Complexity: O(n)

Space Complexity: O(1)
```python
class Solution:
    def closetTarget(self, words: List[str], target: str, startIndex: int) -> int:
        
        if words[startIndex] == target:
            return 0
        n = len(words)
        
        i = (startIndex + 1) % n
        step = 1
        min_step = n
        while i != startIndex:
            if words[i] == target:
                min_step = min( step , min_step ) 
            step += 1
            i = (i + 1) % n
        
        step = 1
        i = (startIndex - 1 + n) % n
        while i != startIndex:
            if words[i] == target:
                min_step = min( step , min_step ) 
            step += 1
            i = (i - 1 + n) % n
        return -1 if min_step == n else min_step
```