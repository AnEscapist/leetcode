# Largest Time for Given Digits

## Description

Given an array of 4 digits, return the largest 24 hour time that can be made.
The smallest 24 hour time is 00:00, and the largest is 23:59.  Starting from 00:00, a time is larger if more time has elapsed since midnight.
Return the answer as a string of length 5.  If no valid time can be made, return an empty string.

**Examples:**

```
Input: [1,2,3,4]
Output: "23:41"
```
```
Input: [5,5,5,5]
Output: ""
```

**Note:**
```
A.length == 4
0 <= A[i] <= 9
```

**Tag:** Math

# Solution 1
This is my naive brute force solution.
```python
class Solution(object):
    def largestTimeFromDigits(self, A):
        """
        :type A: List[int]
        :rtype: str
        """
        res = ''
        a = b = 0
        for i in range(0, 4):
            for j in range(0, 4):
                for x in range(0, 4):
                    for y in range(0, 4):
                        if i != j and i != x and i != y and j != x and j != y and x != y:
                            if A[i] * 10 + A[j] < 24 and A[x] * 10 + A[y] < 60:

                                a = max(A[i] * 1000 + A[j] * 100 + A[x] * 10 + A[y], 0, a)
                                m = str(a // 100)
                                n = str(a % 100)
                                if len(m) == 1:
                                    m = '0' + m
                                if len(n) == 1:
                                    n = '0' + n
                                res = m + ':' + n


        return res
```

# Solution 2
Author: **lee215**, Python 1-line check permutations
```python
class Solution(object):
    def largestTimeFromDigits(self, A):
        return max(['%d%d:%d%d' % t for t in itertools.permutations(A) if t[:2] < (2, 4) and t[2] < 6] or [''])
```
