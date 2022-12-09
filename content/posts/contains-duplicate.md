---
title: "217. Contains Duplicate"
date: 2022-12-09T19:28:08+08:00
draft: false
tags: ["hashmap", "169", "easy"]
series: ["leetcode"]
categories: ["coding"]
---


Solution: hashmap

Code:
```python
# Time Complexity: O(n)
# Space Complexity: O(n)
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        count = {}

        for n in nums:
            if n in count:
                return True
            else:
                count[n] = 1
        return False
```

```python
# Time Complexity: O(n)
# Space Complexity: O(n)
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        return len(set(nums)) != len(nums)
```

