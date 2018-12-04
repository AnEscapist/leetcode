# Valid Parentheses

## Description
Given a string containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:

1. Open brackets must be closed by the same type of brackets.
2. Open brackets must be closed in the correct order.

Note that an empty string is also considered valid.

**Examples**

```
Input: "()"
Output: true

Input: "()[]{}"
Output: true

Input: "(]"
Output: false

Input: "([)]"
Output: false

Input: "{[]}"
Output: true
```

**Method:** STACK

# Solution

```python
class Solution(object):
    def isValid(self, s):
        """
        :type s: str
        :rtype: bool
        """
        left = ['(', '[', '{']
        right = [')', ']', '}']
        match = [['(', ')'], ['[', ']'], ['{', '}']]
        stack = []
        for i in s:
            if i in left:
                stack.append(i)
            else:
                stack.append(i)
                if len(stack) > 1:
                    if not [stack[-2], stack[-1]] in match:
                        return False
                    else:
                        stack.pop()
                        stack.pop()
        return stack == []
```
