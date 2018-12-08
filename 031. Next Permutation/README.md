# Next Permutation

## Description

Implement next permutation, which rearranges numbers into the lexicographically next greater permutation of numbers.
If such arrangement is not possible, it must rearrange it as the lowest possible order (ie, sorted in ascending order).
The replacement must be in-place and use only constant extra memory.

**Examples:**

```
1,2,3 → 1,3,2
3,2,1 → 1,2,3
1,1,5 → 1,5,1
```

# Solution

```python
class Solution(object):
    def nextPermutation(self, nums):
        """
        :type nums: List[int]
        :rtype: void Do not return anything, modify nums in-place instead.
        """
        if len(nums) <= 1:
            return

        i = len(nums) - 1
        while i-1 >= 0 and nums[i] <= nums[i-1]:
            i -= 1

        j = len(nums)-1
        if i > 0:
            while j >= i:
                if nums[j] > nums[i-1]:
                    nums[j], nums[i-1] = nums[i-1], nums[j]
                    break
                j -= 1

        left = i
        right = len(nums)-1
        while left < right:
            nums[left], nums[right] = nums[right], nums[left]
            left += 1
            right -= 1
```
