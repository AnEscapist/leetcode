# Description

Given a matrix of m x n elements (m rows, n columns), return all elements of the matrix in spiral order.

**Examples:**
```
Input:
[
 [ 1, 2, 3 ],
 [ 4, 5, 6 ],
 [ 7, 8, 9 ]
]
Output: [1,2,3,6,9,8,7,4,5]

Input:
[
  [1, 2, 3, 4],
  [5, 6, 7, 8],
  [9,10,11,12]
]
Output: [1,2,3,4,8,12,11,10,9,5,6,7]
```

# Solution

```python
class Solution(object):
    def spiralOrder(self, matrix):
        """
        :type matrix: List[List[int]]
        :rtype: List[int]
        """
        if not matrix: return []
        direction = 0
        left = 0
        right = len(matrix[0])-1
        up = 0
        down = len(matrix)-1
        res = []
        
        while left <= right and up <= down:
            if direction == 0: # from left to right
                for j in range(left, right+1):
                    res.append(matrix[up][j])
                up += 1
            if direction == 1: # from up to bottom
                for i in range(up, down+1):
                    res.append(matrix[i][right])
                right -= 1
            if direction == 2: # from right to left
                for j in range(right, left-1, -1):
                    res.append(matrix[down][j])
                down -= 1
            if direction == 3: # from bottom to up
                for i in range(down, up-1, -1):
                    res.append(matrix[i][left])
                left += 1
            direction = (direction+1) % 4
        return res                 
```    
