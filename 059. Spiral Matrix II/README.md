# Description

Given a positive integer n, generate a square matrix filled with elements from 1 to n2 in spiral order.

**Example**

```
Input: 3
Output:
[
 [ 1, 2, 3 ],
 [ 8, 9, 4 ],
 [ 7, 6, 5 ]
]
```

# Solution:

```python
class Solution(object):
    def generateMatrix(self, n):
        """
        :type n: int
        :rtype: List[List[int]]
        """
        res = [[0 for _ in range(n)] for _ in range(n)]
        
        up = 0
        down = n-1
        left = 0
        right = n-1
        direction = 0
        cur = 1
        while left <= right and up <= down:
            if direction == 0: # from left to right
                for j in range(left, right+1):
                    res[up][j] = cur
                    cur += 1
                up += 1
            if direction == 1: # from up tp bottom
                for i in range(up, down+1):
                    res[i][right] = cur
                    cur += 1
                right -= 1
            if direction == 2: # from right to left
                for j in range(right, left-1, -1):
                    res[down][j] = cur
                    cur += 1
                down -= 1
            if direction == 3: # from bottom to up
                for i in range(down, up-1, -1):
                    res[i][left] = cur 
                    cur += 1
                left += 1
            direction = (direction + 1) % 4
        return res
```
