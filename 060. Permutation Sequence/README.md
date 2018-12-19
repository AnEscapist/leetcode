# Description

The set [1,2,3,...,n] contains a total of n! unique permutations.
By listing and labeling all of the permutations in order, we get the following sequence for n = 3:

1. "123"
2. "132"
3. "213"
4. "231"
5. "312"
6. "321"

Given n and k, return the k-th permutation sequence.

**Note:**

* Given n will be between 1 and 9 inclusive.
* Given k will be between 1 and n! inclusive.

**Examples:**

```
Input: n = 3, k = 3
Output: "213"

Input: n = 4, k = 9
Output: "2314"
```

# Solution 1: backtracking, TLE
```python
class Solution(object):
    def getPermutation(self, n, k):
        """
        :type n: int
        :type k: int
        :rtype: str
        """
        res = []
        visited = [0 for _ in range(n)]
        def dfs(path, res, n):
            if len(path) == n:
                res.append(path)
                return
            for i in range(n):
                if visited[i] == 0:
                    visited[i] = 1
                    dfs(path+str(i+1), res, n)
                    visited[i] = 0
        dfs('', res, n)
        return res[k-1]
                
```

# Solution 2:

```python
class Solution(object):
    def getPermutation(self, n, k):
        """
        :type n: int
        :type k: int
        :rtype: str
        """
        fact = [1 for _ in range(n)]
        for i in range(1, n):
            fact[i] = fact[i-1] * i
        
        res = ''
        first = 0
        k = k-1
        nums = [i for i in range(1, 10)]
        for i in range(n, 0, -1):
            first = k // fact[i-1]
            res = res + str(nums[first])
            k = k % fact[i-1] 
            nums.pop(first)
        return res
```
