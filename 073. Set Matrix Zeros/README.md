# Description

Given a m x n matrix, if an element is 0, set its entire row and column to 0. Do it in-place.

**Examples:**
```
Input: 
[
  [1,1,1],
  [1,0,1],
  [1,1,1]
]
Output: 
[
  [1,0,1],
  [0,0,0],
  [1,0,1]
]

Input: 
[
  [0,1,2,0],
  [3,4,5,2],
  [1,3,1,5]
]
Output: 
[
  [0,0,0,0],
  [0,4,5,0],
  [0,3,1,0]
]
```

# Solution 1: Space complexity: O(m + n)

```python
class Solution(object):
    def setZeroes(self, matrix):
        """
        :type matrix: List[List[int]]
        :rtype: void Do not return anything, modify matrix in-place instead.
        """
        row = len(matrix)
        col = len(matrix[0])
        
        r = [False for _ in range(row)]
        c = [False for _ in range(col)]
        
        for i in range(row):
            for j in range(col):
                if matrix[i][j] == 0:
                    r[i] = True
                    c[j] = True
        
        for i in range(row):
            for j in range(col):
                if r[i] == True or c[j] == True:
                    matrix[i][j] = 0
```

# Solution 2: Space complexity: O(1)

```python
class Solution(object):
    def setZeroes(self, matrix):
        """
        :type matrix: List[List[int]]
        :rtype: void Do not return anything, modify matrix in-place instead.
        """
        row = len(matrix)
        col = len(matrix[0])
        
        r = [False for _ in range(row)]
        c = [False for _ in range(col)]
        
        for i in range(row):
            for j in range(col):
                if matrix[i][j] == 0:
                    matrix[i][j] = 'x'
        
        for i in range(row):
            for j in range(col):
                if matrix[i][j] == 'x':
                    for c in range(col):
                        if c != j and matrix[i][c] != 'x':
                            matrix[i][c] = 0
                    for r in range(row):
                        if r != i and matrix[r][j] != 'x':
                            matrix[r][j] = 0
                        
        for i in range(row):
            for j in range(col):
                if matrix[i][j] == 'x':
                    matrix[i][j] = 0
```
