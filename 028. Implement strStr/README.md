# Implement strStr

## Description

Implement strStr().
Return the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.

**Examples:**

```
Input: haystack = "hello", needle = "ll"
Output: 2

Input: haystack = "aaaaa", needle = "bba"
Output: -1
```

# Solution 1: 20ms

```python
class Solution(object):
    def strStr(self, haystack, needle):
        """
        :type haystack: str
        :type needle: str
        :rtype: int
        """
        if not needle: return 0
        if len(needle) > len(haystack): return -1
        for i in range(0, len(haystack) - len(needle) + 1):
            if haystack[i:i+len(needle)] == needle:
                return i
        return -1
```

# Solution 2: 56ms & 448ms(???)

```python
class Solution(object):
    def strStr(self, haystack, needle):
        """
        :type haystack: str
        :type needle: str
        :rtype: int
        """
        if not needle: return 0
        for i in range(len(haystack)):
            if haystack[i:i+len(needle)] == needle:
                return i
        return -1
```

**Note:** s = 'abc',     s[1:3] = 'bc',  s[1:100] = 'bc', that's why we have solution 2
