# Description

Given a 2D board and a word, find if the word exists in the grid.
The word can be constructed from letters of sequentially adjacent cell, 
where "adjacent" cells are those horizontally or vertically neighboring. The same letter cell may not be used more than once.

**Example:**

```
board =
[
  ['A','B','C','E'],
  ['S','F','C','S'],
  ['A','D','E','E']
]

Given word = "ABCCED", return true.
Given word = "SEE", return true.
Given word = "ABCB", return false.
```

# Solution:

```python
class Solution(object):
    def exist(self, board, word):
        """
        :type board: List[List[str]]
        :type word: str
        :rtype: bool
        """
        row = len(board)
        col = len(board[0])
        res = []
        temp = word
        visited = [[0 for _ in range(col)] for _ in range(row)]

        def dfs(word, res, i, j):
            if ''.join(res) == temp:
                return True

            #up
            if i > 0 and board[i-1][j] == word[0] and visited[i-1][j] == 0:
                res.append(word[0])
                visited[i-1][j] = 1
                if dfs(word[1:], res, i-1, j):
                    return True
                res.pop()
                visited[i-1][j] = 0

            #down
            if i < row-1 and board[i+1][j] == word[0] and visited[i+1][j] == 0:
                res.append(word[0])
                visited[i+1][j] = 1
                if dfs(word[1:], res, i+1, j):
                    return True
                res.pop()
                visited[i+1][j] = 0

            #right 
            if j < col-1 and board[i][j+1] == word[0] and visited[i][j+1] == 0:
                res.append(word[0])
                visited[i][j+1] = 1
                if dfs(word[1:], res, i, j+1):
                    return True
                res.pop()
                visited[i][j+1] = 0

            #left
            if j > 0 and board[i][j-1] == word[0] and visited[i][j-1] == 0:
                res.append(word[0])
                visited[i][j-1] = 1
                if dfs(word[1:], res, i, j-1):
                    return True
                res.pop()
                visited[i][j-1] = 0

        for i in range(row):
            for j in range(col):
                if board[i][j] == word[0]:
                    res.append(board[i][j])
                    visited[i][j] = 1
                    if dfs(word[1:], res, i, j):
                        return True
                    res.pop()
                    visited[i][j] = 0
        return False



```
