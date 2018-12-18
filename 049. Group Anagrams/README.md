# Description

Given an array of strings, group anagrams together.

**Example**

```
Input: ["eat", "tea", "tan", "ate", "nat", "bat"],
Output:
[
  ["ate","eat","tea"],
  ["nat","tan"],
  ["bat"]
]
```

# Solution

```python
class Solution(object):
    def groupAnagrams(self, strs):
        """
        :type strs: List[str]
        :rtype: List[List[str]]
        """
        tmp = dict()
        res = []
        for i, s in enumerate(strs):
            x = ''.join(sorted(s))
            if not x in tmp:
                tmp[x] = [s]
            else:
                tmp[x].append(s)
        for j in tmp.values():
            res.append(j)
        return res
```
