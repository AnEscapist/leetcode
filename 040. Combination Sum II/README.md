# Description

Given a collection of candidate numbers (candidates) and a target number (target), find all unique combinations in candidates where the candidate numbers sums to target.

Each number in candidates may only be used once in the combination.

**Note**

* All numbers (including target) will be positive integers.
* The solution set must not contain duplicate combinations.

**Examples:**

```
Input: candidates = [10,1,2,7,6,1,5], target = 8,
A solution set is:
[
  [1, 7],
  [1, 2, 5],
  [2, 6],
  [1, 1, 6]
]

Input: candidates = [2,5,2,1,2], target = 5,
A solution set is:
[
  [1,2,2],
  [5]
]
```

# Solution

```python
class Solution(object):
    def combinationSum2(self, candidates, target):
        """
        :type candidates: List[int]
        :type target: int
        :rtype: List[List[int]]
        """
        res = []
        candidates.sort()
        
        def dfs(path, target, res, start):
            if sum(path) == target and not path in res:
                res.append(path)
            if sum(path) > target:
                return
            for i in range(start, len(candidates)):
                dfs(path+[candidates[i]], target, res, i+1)
        
        dfs([], target, res, 0)
        return res
```
