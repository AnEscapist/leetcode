# Container With Most Water

## Description 
Given n non-negative integers a1, a2, ..., an , where each represents a point at coordinate (i, ai). 
n vertical lines are drawn such that the two endpoints of line i is at (i, ai) and (i, 0). 
Find two lines, which together with x-axis forms a container, such that the container contains the most water.

**Note:** You may not slant the container and n is at least 2.

![image](https://github.com/AnEscapist/leetcode/blob/master/011.%20Container%20With%20Most%20Water/img/11.PNG)

**Example**

```
Input: [1,8,6,2,5,4,8,3,7]
Output: 49
```

**Tags:** Array, Two Pointers.

# Solution

```python
class Solution(object):
    def maxArea(self, height):
        left, right = 0, len(height) - 1
        res = 0
        while left < right:
            h = min(height[left], height[right])
            area = h * (right - left)
            res = max(area, res)
            if h == height[left]:
                left += 1
            else:
                right -= 1
        return res                          
```
