# ZigZag Conversion

## Description
The string "PAYPALISHIRING" is written in a zigzag pattern on a given number of rows like this: 
(you may want to display this pattern in a fixed font for better legibility)

```
P   A   H   N
A P L S I I G
Y   I   R
```

And then read line by line: "PAHNAPLSIIGYIR"

**Examples:**
```
Input: s = "PAYPALISHIRING", numRows = 3
Output: "PAHNAPLSIIGYIR"
```

```
Input: s = "PAYPALISHIRING", numRows = 4
Output: "PINALSIGYAHRPI"
Explanation:

P     I    N
A   L S  I G
Y A   H R
P     I
```

**Tags**: String, Math

#Solution

```python
class Solution:
    def convert(self, s, numRows):
        """
        :type s: str
        :type numRows: int
        :rtype: str
        """
        if numRows <= 1 or numRows >= len(s):
            return s
        
        arr = [''] * numRows
        x = 2 * numRows - 2
        for i in range(len(s)):
            tmp = i % x
            if tmp < numRows:
                arr[tmp] += s[i]
            else:
                arr[x-tmp] += s[i]
        return ''.join(arr)
```
