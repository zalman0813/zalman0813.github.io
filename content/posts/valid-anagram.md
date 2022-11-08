---
title: "Valid Anagram"
date: 2022-11-08T23:12:06+08:00
draft: false
tags: ["hashmap", "169", "easy"]
series: ["leetcode"]
categories: ["coding"]
---


Solution: hashmap

Code:
```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        
        return Counter(s) == Counter(t)
    
```

Time Complexity: O(n)
Space Complexity: O(n)

Link: https://leetcode.com/problems/valid-anagram/