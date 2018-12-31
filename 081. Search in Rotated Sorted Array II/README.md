# Description

Suppose an array sorted in ascending order is rotated at some pivot unknown to you beforehand.
(i.e., [0,0,1,2,2,5,6] might become [2,5,6,0,0,1,2]).
You are given a target value to search. If found in the array return true, otherwise return false.

**Examples:**

```
Input: nums = [2,5,6,0,0,1,2], target = 0
Output: true

Input: nums = [2,5,6,0,0,1,2], target = 3
Output: false
```

# Solution:
```python
class Solution(object):
    def search(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: bool
        """
        left, right = 0, len(nums)-1
        while left <= right:
            mid = (left+right) // 2
            if nums[mid] == target:
                return True
            if nums[left] == nums[mid] == nums[right]:
                left += 1
                right -= 1
            elif nums[mid] >= nums[left]: #mid in the left part
                if target < nums[mid] and target >= nums[left]:
                    right = mid-1
                else:
                    left = mid+1
            elif nums[mid] <= nums[right]: #mid in the right part
                if target >nums[mid] and target <= nums[right]:
                    left = mid + 1
                else:
                    right = mid - 1
        return False
                    
                
```
