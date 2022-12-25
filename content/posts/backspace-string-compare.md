---
title: "844. Backspace String Compare"
date: 2022-12-25T21:18:36+08:00
draft: false
tags: ["two pointers", "169", "easy"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/backspace-string-compare/

Status: done

Solution: two pointers

Code:
Time Complexity: O(n + m)

Space Complexity: O(1)
```python
class Solution:
    def get_next_valid_char_index(self, str, index):
        backspace_count = 0
        while (index >= 0):
            if str[index] == '#':  # found a backspace character
                backspace_count += 1
            elif backspace_count > 0:  # a non-backspace character
                backspace_count -= 1
            else:
                break

            index -= 1  # skip a backspace or a valid character
        return index

    def backspaceCompare(self, s: str, t: str) -> bool:
        
        s_index = len(s) - 1
        t_index = len(t) - 1

        while s_index >= 0 or t_index >= 0:
            s_index = self.get_next_valid_char_index(s, s_index)
            t_index = self.get_next_valid_char_index(t, t_index)
            
            if s_index < 0 and t_index < 0:
                return True
            if s_index < 0 or t_index < 0:
                return False

            if s[s_index] != t[t_index]:
                return False

            s_index -= 1
            t_index -= 1
        return True
```

