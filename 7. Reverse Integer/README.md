# Reverse Integer

## Description

Given a 32-bit signed integer, reverse digits of an integer

**Examples**

```
Input: 123
Output: 321
```
```
Input: -123
Output: -321
```
```
Input: 120
Output: 21
```
**Tags:** Math

# Solution

```python
class Solution(object):
    def reverse(self, x):
        res = 0
        positive = True
        if x < 0:
            positive = False
        while abs(x) > 0:
            res = res * 10 + abs(x) % 10
            x = abs(x) // 10
        if res > 2 ** 31 -1 or res < -2 ** 31:
            return 0
        return res if positive else -res
```
