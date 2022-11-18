---
title: "383. Ransom Note"
date: 2022-11-18T21:11:51+08:00
draft: false
tags: ["hashmap", "169", "easy"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/ransom-note/

Status: done

Solution: hashmap

Code:
```python
# n - magazine size ,m - ransomNote size
# Time Complexity: O(n + m) -> O(n), if true, n >= m
# Space Complexity: O(n)
class Solution:
    def canConstruct(self, ransomNote: str, magazine: str) -> bool:
        if len(ransomNote) > len(magazine):
            return False
        
        mMap = {}
        for c in magazine:
            mMap[c] = 1 + mMap.get(c, 0)
        
        for char in ransomNote:
            if char in mMap and mMap[char] > 0:
                mMap[char] -= 1
            else:
                return False            
        return True
```



