# Description

Implement pow(x, n), which calculates x raised to the power n (x^n).

**Examples:**
```
Input: 2.00000, 10
Output: 1024.00000

Input: 2.10000, 3
Output: 9.26100

Input: 2.00000, -2
Output: 0.25000
Explanation: 2-2 = 1/22 = 1/4 = 0.25
```

# Solution

```python
class Solution(object):
    def myPow(self, x, n):
        """
        :type x: float
        :type n: int
        :rtype: float
        """
        if n == 0:
            return 1
        if n < 0:
            x = 1 / x
            n = -n
        if n % 2 == 1:
            return x * self.myPow(x, n - 1)
        return self.myPow(x*x, n//2)
            
```
