# Description

Given an integer array nums, find the contiguous subarray (containing at least one number) 
which has the largest sum and return its sum.

**Example:**
```
Input: [-2,1,-3,4,-1,2,1,-5,4],
Output: 6
Explanation: [4,-1,2,1] has the largest sum = 6.
```

# Solution

```python
class Solution(object):
    def maxSubArray(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        cur_max = nums[0]
        res = nums[0]
        for i in nums[1:]:
            cur_max = max(cur_max+i, i)
            res = max(res, cur_max)
        return res
```
