# 3Sum

## Description
Given an array nums of n integers, are there elements a, b, c in nums such that a + b + c = 0? 
Find all unique triplets in the array which gives the sum of zero.

**Note:** The solution set must not contain duplicate triplets.

**Example:**
```
Given array nums = [-1, 0, 1, 2, -1, -4],

A solution set is:
[
  [-1, 0, 1],
  [-1, -1, 2]
]
```

# Solution 1
TLE, for every num[i], do 2Sum for the rest of nums. 311/313 test cases passed.

```python
class Solution(object):
    def threeSum(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """
        res = []
        for i in range(len(nums)):
            sublist = []
            a = nums[i]
            d = list()
            for j in range(len(nums)):
                if j != i:
                    if -a-nums[j] in d:
                        sublist = [-a-nums[j], nums[j], a]
                        sublist.sort()
                        if not sublist in res:
                            res.append(sublist)
                    else:
                        d.append(nums[j])
            
        return res
            
```

# Solution 2

```python
class Solution(object):
    def threeSum(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """
        res = []
        nums.sort()
        for i in range(len(nums)-2):
            if i > 0 and nums[i] == nums[i-1]:
                continue
            left, right = i+1, len(nums) - 1
            while left < right:
                s = nums[i] + nums[left] + nums[right]
                
                if s < 0:
                    left += 1
                if s > 0:
                    right -= 1
                if s == 0:
                    res.append([nums[i], nums[left], nums[right]])
                    while left < right and nums[left] == nums[left+1]:
                        left += 1
                    while left < right and nums[right] == nums[right-1]:
                        right -= 1
                    left += 1
                    right -= 1
        return res
```



