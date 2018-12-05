# Swap Node in Pairs

## Description
Given a linked list, swap every two adjacent nodes and return its head.

**Example**
```
Given 1->2->3->4, you should return the list as 2->1->4->3.
```

# Solution

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def swapPairs(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        if not head or not head.next:
            return head
        dummy = ListNode(-1)
        dummy.next = head
        
        pre = dummy
        l, r = head, head.next
        
        while pre.next and pre.next.next:
            pre.next = r
            l.next = r.next
            r.next = l
            
            pre = l
            l = l.next
            if l:
                r = l.next
        return dummy.next
```
