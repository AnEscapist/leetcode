# String to Integer (atoi)

## Description
Implement **atoi** which converts a string to an integer.

The function first discards as many whitespace characters as necessary until the first non-whitespace character is found. Then, starting from this character, takes an optional initial plus or minus sign followed by as many numerical digits as possible, and interprets them as a numerical value.

The string can contain additional characters after those that form the integral number, which are ignored and have no effect on the behavior of this function.

If the first sequence of non-whitespace characters in str is not a valid integral number, or if no such sequence exists because either str is empty or it contains only whitespace characters, no conversion is performed.

If no valid conversion could be performed, a zero value is returned.

## Note

```
Only the space character ' ' is considered as whitespace character.
Assume we are dealing with an environment which could only store integers within the 32-bit signed integer range: [−2^31,  2^31 − 1]. 
If the numerical value is out of the range of representable values, INT_MAX (231 − 1) or INT_MIN (−231) is returned.
```

## Examples
```
Input: "42"
Output: 42
```
```
Input: "   -42"
Output: -42
Explanation: The first non-whitespace character is '-', which is the minus sign.
             Then take as many numerical digits as possible, which gets 42.
```
```
Input: "4193 with words"
Output: 4193
Explanation: Conversion stops at digit '3' as the next character is not a numerical digit.
```

```
Input: "words and 987"
Output: 0
Explanation: The first non-whitespace character is 'w', which is not a numerical 
             digit or a +/- sign. Therefore no valid conversion could be performed.
```

# Solution

```python
class Solution(object):
    def myAtoi(self, str):
        INT_MAX = 2 ** 31 - 1
        INT_MIN = -2 ** 31
        s = str.strip()
        positive = 1
        res = 0
        if not s:
            return res
        elif s[0] in '+-':
            positive = -1 if s[0] == '-' else 1
            try:
                s = s[1:]
            except IndexError:
                return 0
        elif s[0] >= '0' and s[0] <= '9':
            pass
        else:
            return 0

        for x in s:
            if x >= '0' and x <= '9':
                res = 10 * res + ord(x) - ord('0')
            else:
                break
        res = positive * res
        res = INT_MAX if res > INT_MAX else res
        res = INT_MIN if res < INT_MIN else res
        return res
            

```
