# Count and Say

## Description

The count-and-say sequence is the sequence of integers with the first five terms as following:

```
1.     1
2.     11
3.     21
4.     1211
5.     111221
```

# Solution

```python
class Solution(object):
    def countAndSay(self, n):
        """
        :type n: int
        :rtype: str
        """
        dp = [''] * n
        dp[0] = '1'
        for i in range(1, n):
            left, right = 0, 0
            while right < len(dp[i-1]):
                
                while right < len(dp[i-1]) and dp[i-1][left] == dp[i-1][right]:
                    right += 1
                dp[i] = dp[i] + str(right - left) + str(dp[i-1][left])
                left = right
        return dp[n-1]
```
