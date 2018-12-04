# 3Sum Closest

## Description
Given an array nums of n integers and an integer target, find three integers in nums such that the sum is closest to target. 
Return the sum of the three integers. You may assume that each input would have exactly one solution.

**Example**
```
Given array nums = [-1, 2, 1, -4], and target = 1.
The sum that is closest to the target is 2. (-1 + 2 + 1 = 2).
```

**Method:** Similar to 015.3Sum

# Solution

```python
class Solution(object):
    def threeSumClosest(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: int
        """
        nums.sort()
        if len(nums) < 3:
            return None
        dif = 2**31 - 1
        res = 0
        for i in range(len(nums) - 2):
            left, right = i+1, len(nums) - 1
            while left < right:
                s = nums[i] + nums[left] + nums[right]
                if s == target:
                    return s
                elif s > target:
                    if dif > abs(s - target):
                        dif = abs(s-target)
                        res = s
                    right -= 1
                else:
                    if dif > abs(s - target):
                        dif = abs(s-target)
                        res = s
                    left += 1
                        
        return res
```
