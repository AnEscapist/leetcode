# Longest Common Prefix

## Description

Write a function to find the longest common prefix string amongst an array of strings.
If there is no common prefix, return an empty string "".

**Examples:**
```
Input: ["flower","flow","flight"]
Output: "fl"

Input: ["dog","racecar","car"]
Output: ""
Explanation: There is no common prefix among the input strings.
```

# Solution 1: 44ms
```python
class Solution(object):
    def longestCommonPrefix(self, strs):
        """
        :type strs: List[str]
        :rtype: str
        """
        res = ''
        if not strs: return res
        for i in range(len(strs[0])):
            for s in strs[1:]:
                if i >= len(s) or s[i] != strs[0][i]:
                    return res
            res += strs[0][i]
        return res
       
```

# Solution 2: 20ms

```python
class Solution(object):
    def longestCommonPrefix(self, strs):
        """
        :type strs: List[str]
        :rtype: str
        """
        if not strs or len(strs) == 0:
            return ''
        res = ''
        strs = sorted(strs)
        a, b = strs[0], strs[-1]
        for i in range(len(a)):
            if a[i] == b[i]:
                res += a[i]
            else:
                break
        return res
        
```
