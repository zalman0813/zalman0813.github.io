---
title: "252. Meeting Rooms"
date: 2022-12-19T23:38:29+08:00
draft: false
tags: ["interval", "169", "easy"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/meeting-rooms/

Status: done

Solution: interval

Code:
```python
class Solution:
    def meetingRooms(self, intervals: List[int]) -> bool:
        intervals.sort(lambda x: x.start)
        for i in range(1, len(intervals)):
            i1 = intervals[i - 1]
            i2 = intervals[i]
            if i1.end > i2.start:
                return False
        return True
```