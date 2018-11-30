# Longest Palindromic Substring

##Description

Given a string **s**, find the longest palindromic substring in **s**. You may assume that the maximum length of **s** is 1000.

**Examples:**

```
Input: "babad"
Output: "bab"
Note: "aba" is also a valid answer.
```
```
Input: "cbbd"
Output: "bb"
```

**Tags:** String, Dynamic Programming

# Solution

```python
class Solution(object):
    def longestPalindrome(self, s):
    
        def is_Pal(s, left, right):
            while left >= 0 and right < len(s) and s[left:right+1] == s[left:right+1][::-1]:
                left -= 1
                right += 1
            return s[left+1:right]
            
        max_len = 0
        res = ''
        for i in range(len(s)):
            x = is_Pal(s, i, i)
            if max_len < len(x):
                res = x
                max_len = len(x)
        for i in range(len(s)):
            x = is_Pal(s, i, i+1)
            if max_len < len(x):
                res = x
                max_len = len(x)
        return res
            
```
