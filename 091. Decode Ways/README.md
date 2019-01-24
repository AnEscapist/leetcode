# Description
A message containing letters from A-Z is being encoded to numbers using the following mapping:
```
'A' -> 1
'B' -> 2
...
'Z' -> 26
```
Given a non-empty string containing only digits, determine the total number of ways to decode it.

**Examples:**
```
Input: "12"
Output: 2
Explanation: It could be decoded as "AB" (1 2) or "L" (12).

Input: "226"
Output: 3
Explanation: It could be decoded as "BZ" (2 26), "VF" (22 6), or "BBF" (2 2 6).
```

# Solution
    # DP
    # dp[i] means the number of ways to decode s[:i]
    # dp[i] = dp[i-1] if s[i-1] != '0'
    #       + dp[i-2] if '10' <= s[i-2:i] <= '26'

```python
class Solution:
    def numDecodings(self, s):
        """
        :type s: str
        :rtype: int
        """
        if not s or s[0] == 0:
            return 0
        dp = [0] * (len(s) + 1)
        dp[0] = 1
        for i in range(1, len(s)+1):
            if s[i-1] != '0':
                dp[i] = dp[i-1]
            if i > 1 and '10' <= s[i-2:i] <= '26':
                dp[i] += dp[i-2]
        return dp[-1]
                
```
