# Find First and Last Position of Element in Sorted Array

## Description

Given an array of integers nums sorted in ascending order, find the starting and ending position of a given target value.
Your algorithm's runtime complexity must be in the order of O(log n).
If the target is not found in the array, return [-1, -1].

**Examples:**

```
Input: nums = [5,7,7,8,8,10], target = 8
Output: [3,4]

Input: nums = [5,7,7,8,8,10], target = 6
Output: [-1,-1]
```
# Solution 1:  Q: Is the time complexity O(log n)?

```python
class Solution:
    def searchRange(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        left = 0
        right = len(nums) - 1
        while left <= right:
            mid = (left + right) // 2
            if target > nums[mid]:
                left = mid + 1
            if target < nums[mid]:
                right = mid - 1
            if target == nums[mid]:
                left, right = mid, mid
                while left >= 0 and target == nums[left] :
                    left -= 1
                while right <= len(nums)-1 and target == nums[right]:
                    right += 1
                break
                
        return [-1, -1] if left > right else [left+1, right-1]
```

# Solution 2:

```python
class Solution(object):
    def searchRange(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        a, b = -1, -1
        left = 0
        right = len(nums) - 1
        while left <= right:
            mid = (left + right) // 2
            if target > nums[mid]:
                left = mid + 1
            elif target < nums[mid]:
                right = mid - 1
            else:
                break
        if left > right:
            return [-1, -1]
        m = mid
        left, right = 0, m
        while left < right:
            m = (left + right) // 2
            if nums[m] != nums[mid]:
                left = m + 1
            else:
                right = m
        a = left
        
        left, right = mid, len(nums) - 1
        while left <= right:
            m = (left + right) // 2
            if nums[m] != nums[mid]:
                right = m - 1
            else:
                left = m + 1
        b = right
        return [a, b]
```
