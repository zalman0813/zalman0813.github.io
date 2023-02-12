---
title: "767. Reorganize String"
date: 2023-02-12T15:16:54+08:00
draft: false
tags: ["top k elements", "maxheap","medium"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/reorganize-string/

Solution: top k elements

Code:
```python
# Time Complexity: O(nlogc). Due to c bounded by the size of the alphabet, space is O(n).
# Space Complexity: O(c). Due to c bounded by the size of the alphabet, space is O(1).
from collections import Counter
import heapq
class Solution:
    def reorganizeString(self, s: str) -> str:

        char_counter = Counter(s)
        most_freq_chars = []

        for char, freq in char_counter.items():
            heapq.heappush(most_freq_chars, [-freq, char])
        
        result = ""
        previous = None

        while len(most_freq_chars) > 0:            
            count, char = heapq.heappop(most_freq_chars)
            result += char
            count += 1

            if previous:
                heapq.heappush(most_freq_chars, previous)
                previous = None
            
            if count != 0:
                previous = [count, char]
        if previous:
            return ""
        return result

```

