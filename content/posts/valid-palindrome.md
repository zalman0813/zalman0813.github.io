---
title: "Valid Palindrome"
date: 2022-11-04T21:07:32+08:00
draft: false
tags: ["two point", "169", "easy"]
series: ["leetcode"]
categories: ["coding"]
---


Solution: Two Pointer

Code:
```python
class Solution:
    def isPalindrome(self, s: str) -> bool:
        
        l, r = 0, len(s) - 1
        
        while l < r:
            while l < r and not self.alphaNum(s[l]):
                l += 1
            while l < r and not self.alphaNum(s[r]):
                r-=1
            if s[l].lower() != s[r].lower():
                return False
            l, r = l+1, r-1
        return True        
        
    def alphaNum(self, c):
        return (ord('A') <= ord(c) <= ord('Z') or
                ord('a') <= ord(c) <= ord('z') or
                ord('0') <= ord(c) <= ord('9')
               )
    
```

Time Complexity: O(n)

Space Complexity: O(1)

Link: https://leetcode.com/problems/valid-palindrome/