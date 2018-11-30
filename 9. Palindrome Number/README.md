# Palindrome Number

## Description

Determine whether an integer is a palindrome. An integer is a palindrome when it reads the same backward as forward.

**Examples**
```
Input: 121
Output: true
```

```
Input: -121
Output: false
Explanation: From left to right, it reads -121. From right to left, it becomes 121-. Therefore it is not a palindrome.
```

# Solution

```python
class Solutin(object):
    def isPalindrome(self, x):
        if x < 0:
            return False
        return str(x) == str(x)[::-1]

```
