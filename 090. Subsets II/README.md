# Description

Given a collection of integers that might contain duplicates, nums, return all possible subsets (the power set).

Note: The solution set must not contain duplicate subsets.

**Example**

```
Input: [1,2,2]
Output:
[
  [2],
  [1],
  [1,2,2],
  [2,2],
  [1,2],
  []
]
```

# Solution

```python
class Solution(object):
    def subsetsWithDup(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """
        res = []
        nums.sort()
        def dfs(res, path, nums):
            if not path in res:
                res.append(path)
            for i in range(len(nums)):
                dfs(res, path+[nums[i]], nums[i+1:])
        dfs(res, [], nums)
        return res
```
