---
title: "5. Longest Palindromic Substring"
date: 2023-04-09T16:41:07+08:00
draft: false
tags: ["169", "medium", "dp", "lps"]
series: ["leetcode"]
categories: ["coding"]
---
Link: https://leetcode.com/problems/longest-palindromic-substring/


Code:
```python
# Time Complexity: O(n^2)
# Space Complexity: O(n)
class Solution:
    def longestPalindrome(self, s: str) -> str:
        
        res = ""
        resLen = 0
        
        for i in range(len(s)):
            # odd length
            l, r = i, i
            while l >= 0 and r < len(s) and s[l] == s[r]:
                
                if r - l + 1 > resLen:
                    res = s[l:r+1]
                    resLen = r - l + 1
                l-=1
                r+=1
            
            # even length
            l, r = i, i+1
            while l >= 0 and r < len(s) and s[l] == s[r]:
                if r - l + 1 > resLen:
                    res = s[l:r+1]
                    resLen = r - l + 1
                l-=1
                r+=1
        return res

```



