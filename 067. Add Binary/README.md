# Description

Given two binary strings, return their sum (also a binary string).
The input strings are both non-empty and contains only characters 1 or 0.

**Examples:**

```
Input: a = "11", b = "1"
Output: "100"

Input: a = "1010", b = "1011"
Output: "10101"
```

```python
class Solution(object):
    def addBinary(self, a, b):
        """
        :type a: str
        :type b: str
        :rtype: str
        """
        res = ''
        i, j, carry = len(a)-1, len(b)-1, 0
        while i >= 0 or j >= 0 or carry > 0:
            carry += int(a[i]) if i >= 0 else 0
            carry += int(b[j]) if j >= 0 else 0
            res = str(carry%2) + res
            i, j, carry = i-1, j-1, carry // 2
        return res
```
