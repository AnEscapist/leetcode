# Description

Given two integers n and k, return all possible combinations of k numbers out of 1 ... n.

**Example:**

```
Input: n = 4, k = 2
Output:
[
  [2,4],
  [3,4],
  [2,3],
  [1,2],
  [1,3],
  [1,4],
]
```

# Solution

```python
class Solution(object):
    def combine(self, n, k):
        """
        :type n: int
        :type k: int
        :rtype: List[List[int]]
        """
        res = []
        
        def dfs(res, path, array):
            if len(path) == k:
                res.append(path)
                return
            for i in range(len(array)):
                dfs(res, path+[array[i]], array[i+1:])
        array = [i+1 for i in range(n)]
        dfs(res, [], array)
        return res
                
```
