# Merge Two Sorted List

## Description
Merge two sorted linked lists and return it as a new list. 
The new list should be made by splicing together the nodes of the first two lists.

**Example**
```
Input: 1->2->4, 1->3->4
Output: 1->1->2->3->4->4
```

# Solution

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def mergeTwoLists(self, l1, l2):
        """
        :type l1: ListNode
        :type l2: ListNode
        :rtype: ListNode
        """
        cur = dummy = ListNode(-1)
        
        while l1 or l2:
            if not l2: 
                cur.next = l1
                break
            if not l1: 
                cur.next = l2
                break
            if l1.val < l2.val:
                cur.next = l1
                l1 = l1.next
            else:
                cur.next = l2
                l2 = l2.next
            cur = cur.next
        return dummy.next
```
