# Description

Write a function that reverses a string. The input string is given as an array of characters char[].
Do not allocate extra space for another array, you must do this by modifying the input array in-place with O(1) extra memory.
You may assume all the characters consist of printable ascii characters.

**Examples**

```
Input: ["h","e","l","l","o"]
Output: ["o","l","l","e","h"]

Input: ["H","a","n","n","a","h"]
Output: ["h","a","n","n","a","H"]
```

# Solution:

```python
class Solution(object):
    def reverseString(self, s):
        """
        :type s: str
        :rtype: str
        """
        left = 0
        right = len(s) - 1
        while left < right:
            s[left], s[right] = s[right], s[left]
            left += 1
            right -= 1
```

```python
class Solution(object):
    def reverseString(self, s):
        """
        :type s: str
        :rtype: str
        """
        return s[::-1]
```
