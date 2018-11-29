# Longest Substring Without Repeating Characters

## Description
Given a string, find the length of the **longest substring** without repeating characters.

**Examples**
```
Input: "abcabcbb"
Output: 3 
Explanation: The answer is "abc", with the length of 3. 
```
```
Input: "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
```
```
Input: "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3. 
             Note that the answer must be a substring, "pwke" is a subsequence and not a substring.
```

**Tags:** Hash Table, Two Pointers, String

# Solution

```python
class Solution(object):
    def lengthOfLongestSubstring(self, s):
        d = dict()
        res = start = 0
        for i in range(len(s)):
            if s[i] in d:
                start = d[s[i]] + 1 if d[s[i]] + 1 > start else start
                d[s[i]] = i
                res = max(res, i - start + 1)
            else:
                d[s[i]] = i
                res = max(res, i - start + 1)
        return res

```
