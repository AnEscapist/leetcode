# Description

Given a collection of numbers that might contain duplicates, return all possible unique permutations.

**Examples**

```
Input: [1,1,2]
Output:
[
  [1,1,2],
  [1,2,1],
  [2,1,1]
]
```

# Solution

```python
class Solution(object):
    def permuteUnique(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """
        res = []
        visited = [0 for _ in range(len(nums))]
        def dfs(path, res):
            if len(path) == len(nums) and not path in res:
                res.append(path)
            for i in range(len(nums)):
                if visited[i] == 0:
                    visited[i] = 1
                    dfs(path + [nums[i]], res)
                    visited[i] = 0
                
        dfs([], res)
        return res
```

