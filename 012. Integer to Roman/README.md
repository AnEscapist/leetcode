# Integer to Roman

## Description
Roman numerals are represented by seven different symbols: I, V, X, L, C, D and M.
```
Symbol       Value
I             1
V             5
X             10
L             50
C             100
D             500
M             1000
```
For example, two is written as **II* in Roman numeral, just two one's added together. 
Twelve is written as, **XII**, which is simply **X + II**. The number twenty seven is written as **XXVII**, which is **XX + V + II**.

```
I can be placed before V (5) and X (10) to make 4 and 9. 
X can be placed before L (50) and C (100) to make 40 and 90. 
C can be placed before D (500) and M (1000) to make 400 and 900.
```
Given an integer, convert it to a roman numeral. Input is guaranteed to be within the range from 1 to 3999.

**Examples:**
```
Input: 3
Output: "III"
Input: 4
Output: "IV"
Input: 9
Output: "IX"
Input: 58
Output: "LVIII"
Explanation: L = 50, V = 5, III = 3.
Input: 1994
Output: "MCMXCIV"
Explanation: M = 1000, CM = 900, XC = 90 and IV = 4.
```

# Solution
```python
class Solution(object):
    def intToRoman(self, num):
        """
        :type num: int
        :rtype: str
        """
        n = [1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1]
        r = ['M', 'CM', 'D', 'CD', 'C', 'XC', 'L', 'XL', 'X', 'IX', 'V', 'IV', 'I']
        res = ''
        while num > 0:
            for i in range(len(n)):
                if num // n[i] != 0:
                    x = num // n[i]
                    for j in range(x):
                        res = res + r[i]
                    num = num % n[i]
        return res
```



