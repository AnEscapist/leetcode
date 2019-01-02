# Description

Given a linked list and a value x, partition it such that all nodes less than x come before nodes greater than or equal to x.
You should preserve the original relative order of the nodes in each of the two partitions.

**Example:**

```
Input: head = 1->4->3->2->5->2, x = 3
Output: 1->2->2->4->3->5
```

# Solution

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def partition(self, head, x):
        """
        :type head: ListNode
        :type x: int
        :rtype: ListNode
        """
        dummy1 = ListNode(-1)
        h1 = dummy1
        dummy2 = ListNode(-2)
        h2 = dummy2
        
        cur = head
        while cur:
            if cur.val < x:
                h1.next = cur
                cur = cur.next
                h1 = h1.next
            else:
                h2.next = cur
                cur = cur.next
                h2 = h2.next
        h1.next = dummy2.next
        h2.next = None
        return dummy1.next
```
