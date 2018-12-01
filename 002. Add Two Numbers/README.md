# Add Two Numbers

## Description

You are given two **non-empty** linked lists representing two non-negative integers. 
The digits are stored in **reverse order** and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

**Example**
```
Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
Output: 7 -> 0 -> 8
Explanation: 342 + 465 = 807.
```

**Tags:** Linked List, Math

# Solution

```python
#Definition for singly-linked list.
#class ListNode:
#   def __init__(self, x):
#       self.val = x
#       self.next = None

class Solution:
    def addTwoNumbers(self, l1, l2):
        dummy = cur = ListNode(-1)
        carry = 0
        while l1 or l2:
            a = l1.val if l1 else 0
            b = l2.val if l2 else 0
            s = a + b + carry
            cur.next = ListNode(s % 10)
            carry = s // 10
            cur = cur.next
            
            if l1:
                l1 = l1.next
            if l2:
                l2 = l2.next
        if carry:
            cur.next = ListNode(1)
        return dummy.next
        
```

