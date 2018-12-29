# Description
Given a set of distinct integers, nums, return all possible subsets (the power set).

**Example:**
```
Input: nums = [1,2,3]
Output:
[
  [3],
  [1],
  [2],
  [1,2,3],
  [1,3],
  [2,3],
  [1,2],
  []
]
```

# Solution:

```python
class Solution(object):
    def subsets(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """
        res = []
        
        def dfs(res, path, nums):
            if not path in res:
                res.append(path)
                
            for i in range(len(nums)):
                dfs(res, path+[nums[i]], nums[i+1:])
        dfs(res, [], nums)
        return res
```
