# Letter Combinations of a Phone Number

## Description

Given a string containing digits from 2-9 inclusive, return all possible letter combinations that the number could represent.
A mapping of digit to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.

![image](https://github.com/AnEscapist/leetcode/blob/master/017.%20Letter%20Combinations%20of%20a%20Phone%20Number/img/17.PNG?raw=true)

**Example:**

```
Input: "23"
Output: ["ad", "ae", "af", "bd", "be", "bf", "cd", "ce", "cf"].
```

#Solution: Backtracking

```python
class Solution(object):
    def letterCombinations(self, digits):
        """
        :type digits: str
        :rtype: List[str]
        """
        d = {
            '2': 'abc',
            '3': 'def',
            '4': 'ghi',
            '5': 'jkl',
            '6': 'mno',
            '7': 'pqrs',
            '8': 'tuv',
            '9': 'wxyz'
        }
        
        if not digits:
            return []
        
        res = []
        def dfs(res, num, substr):
            if num == len(digits):
                res.append(substr)
            else:
                for i in d[digits[num]]:
                    dfs(res, num+1, substr + i)
        dfs(res, 0, '')
        return res
        
```
