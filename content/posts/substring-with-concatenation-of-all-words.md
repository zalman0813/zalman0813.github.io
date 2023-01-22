---
title: "30. Substring With Concatenation of All Words"
date: 2023-01-22T19:31:04+08:00
draft: false
tags: ["sliding windows", "hard"]
series: ["leetcode"]
categories: ["coding"]
---

Link: https://leetcode.com/problems/substring-with-concatenation-of-all-words

Solution: sliding windows

Code:
```python
# O(n∗m∗len) where ‘n’ is the number of characters in the given string, ‘m’ is the total number of words, and ‘len’ is the length of a word.
# Space Complexity: O(n+m)
class Solution:
    def findSubstring(self, str1: str, words: List[str]) -> List[int]:
        result_indices = []
        # TODO: Write your code here
        
        word_freq = Counter(words)
        word_count = len(words)
        word_length = len(words[0])

        for i in range((len(str1) - word_count * word_length) + 1):
            word_seen = {}
            for j in range(word_count):
                next_word_index = i + j * word_length
                # if not equal to the word
                # Get the next word from the string
                word = str1[next_word_index: next_word_index + word_length]
                if word not in word_freq:  # Break if we don't need this word
                    break
            
                word_seen[word] = 1 + word_seen.get(word, 0)
                # if mapping more than counts
                if word_seen[word] > word_freq.get(word, 0):
                    break

                # append
                if j + 1 == word_count:
                    result_indices.append(i)


        return result_indices
    
```





