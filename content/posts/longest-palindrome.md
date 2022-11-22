---
title: "409. Longest Palindrome"
date: 2022-11-22T23:12:44+08:00
draft: false
tags: ["hashmap", "169", "easy"]
series: ["leetcode"]
categories: ["coding"]
---
Link: https://leetcode.com/problems/longest-palindrome/

Solution: hashmap

Code:
```python
# Time Complexity: O(n)
# Space Complexity: O(n)
class Solution:
    def longestPalindrome(self, s: str) -> int:
        if len(s) == 1: return 1
        
        char_freq = collections.Counter(s)
        
        length = 0
        
        for count in char_freq.values():
            # add max even count of all chars
            length += count // 2 * 2
        
        # if string includes odd char,length + 1 [can choose only one odd count]
        # if total chars are event counts, return original string length
        return min(length + 1, len(s))
```



