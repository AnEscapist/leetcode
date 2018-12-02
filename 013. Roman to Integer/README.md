# Roman to Integer

## Description

Similar to Question 12 (convert integer to roman), just convert roman to integer.

**Examples:**

```
Input: "III"
Output: 3
Input: "IV"
Output: 4
Input: "IX"
Output: 9
Input: "LVIII"
Output: 58
Explanation: L = 50, V= 5, III = 3.
Input: "MCMXCIV"
Output: 1994
Explanation: M = 1000, CM = 900, XC = 90 and IV = 4.
```

# Solution

```python
class Solution(object):
    def romanToInt(self, s):
        """
        :type s: str
        :rtype: int
        """
        d = {
            'M': 1000,
            'CM': 900,
            'D': 500,
            'CD': 400,
            'C': 100,
            'XC':90,
            'L': 50,
            'XL': 40,
            'X': 10,
            'IX': 9,
            'V': 5,
            'IV': 4,
            'I': 1
        }
        left, right = 0, 1
        res = 0
        while left < len(s):
            if right < len(s):
                if s[left:right+1] in d.keys():
                    res += d[s[left:right+1]]
                    left += 2
                    right += 2
                else:
                    res += d[s[left]]
                    left += 1
                    right += 1
            else:
                res += d[s[left]]
                left += 1
                right += 1
    
        return res
            
```
