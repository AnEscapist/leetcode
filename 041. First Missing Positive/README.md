# Description

Given an unsorted integer array, find the smallest missing positive integer.

**Examples:**

```
Input: [1,2,0]
Output: 3

Input: [3,4,-1,1]
Output: 2

Input: [7,8,9,11,12]
Output: 1
```

# Solution:

```python
class Solution(object):
    def firstMissingPositive(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        n = len(nums)
        for i in range(n):
            if nums[i] <= 0:
                nums[i] = n+1
        for i in range(n):
            if abs(nums[i]) <= n:
                cur = abs(nums[i]) - 1
                nums[cur] = -abs(nums[cur])
        for i in range(n):
            if nums[i] > 0:
                return i+1
        return n + 1
```
