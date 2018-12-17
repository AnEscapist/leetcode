# Description
Given two non-negative integers num1 and num2 represented as strings, 
return the product of num1 and num2, also represented as a string.

**Examples:**
```
Input: num1 = "2", num2 = "3"
Output: "6"

Input: num1 = "123", num2 = "456"
Output: "56088"
```

**Notes:**
* The length of both num1 and num2 is < 110.
* Both num1 and num2 contain only digits 0-9.
* Both num1 and num2 do not contain any leading zero, except the number 0 itself.
* You must not use any built-in BigInteger library or convert the inputs to integer directly.

# Solution

```python
class Solution(object):
    def multiply(self, num1, num2):
        """
        :type num1: str
        :type num2: str
        :rtype: str
        """
        res = 0
        for i, n1 in enumerate(num2[::-1]):
            cur = 0
            carry = 0
            for j, n2 in enumerate(num1[::-1]):
                m = (ord(n1) - ord('0')) * (ord(n2) - ord('0'))
                first, second = m // 10, m % 10
                cur += (second + carry) * (10 ** j)
                carry = first
            cur += carry * (10 ** len(num1))
            res += cur * (10 ** i)
        return str(res)
```
