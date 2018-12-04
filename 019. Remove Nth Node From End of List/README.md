# Remove Nth Node From End of List

## Discription
Given a linked list, remove the n-th node from the end of list and return its head.

**Example**

```
Given linked list: 1->2->3->4->5, and n = 2.
After removing the second node from the end, the linked list becomes 1->2->3->5.
```

# Solution

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def removeNthFromEnd(self, head, n):
        """
        :type head: ListNode
        :type n: int
        :rtype: ListNode
        """
        if not head or not head.next:
            return None
        
        dummy = ListNode(-1)
        dummy.next = head   
        pre = dummy
        s = head
        f = head
        for i in range(n):
            f = f.next
        while f:
            s = s.next
            f = f.next
            pre = pre.next
        pre.next = s.next
        return dummy.next
```
