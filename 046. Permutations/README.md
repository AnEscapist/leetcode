# Description

Given a collection of distinct integers, return all possible permutations.

**Example:**

```
Input: [1,2,3]
Output:
[
  [1,2,3],
  [1,3,2],
  [2,1,3],
  [2,3,1],
  [3,1,2],
  [3,2,1]
]
```

# Solution 1:

```python
from itertools import permutations
class Solution(object):
    def permute(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """
        return list(permutations(nums))
```

# Solution 2:

```python
class Solution(object):
    def permute(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """
        res = []
        
        def dfs(path):
            if len(path) == len(nums):
                res.append(path)
            for i in range(len(nums)):
                if not nums[i] in path:
                    dfs(path + [nums[i]])
        dfs([])
        return res
```
