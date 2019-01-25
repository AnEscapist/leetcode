#Description

Given a string containing only digits, restore it by returning all possible valid IP address combinations.

**Example:**
```
Input: "25525511135"
Output: ["255.255.11.135", "255.255.111.35"]
```

# Solution
```python
class Solution(object):
    def restoreIpAddresses(self, s):
        """
        :type s: str
        :rtype: List[str]
        """
        res = []
        def dfs(res, path, s):
            if len(s) > (4 - len(path)) * 3:
                return
            
            if not s and len(path) == 4:
                res.append('.'.join(path))
                return
            
            
            for i in range(min(3, len(s))):
                cur = s[:i+1]
                if (cur[0] == '0' and len(cur) >= 2) or int(cur) > 255:
                    continue
                dfs(res, path+[cur], s[i+1:])
        dfs(res, [], s)
        return res
```
