# Description

Given a linked list, rotate the list to the right by k places, where k is non-negative.

**Examples:**

```
Input: 1->2->3->4->5->NULL, k = 2
Output: 4->5->1->2->3->NULL
Explanation:
rotate 1 steps to the right: 5->1->2->3->4->NULL
rotate 2 steps to the right: 4->5->1->2->3->NULL

Input: 0->1->2->NULL, k = 4
Output: 2->0->1->NULL
Explanation:
rotate 1 steps to the right: 2->0->1->NULL
rotate 2 steps to the right: 1->2->0->NULL
rotate 3 steps to the right: 0->1->2->NULL
rotate 4 steps to the right: 2->0->1->NULL
```

# Solution

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def rotateRight(self, head, k):
        """
        :type head: ListNode
        :type k: int
        :rtype: ListNode
        """
        if k == 0 or not head:
            return head
        cur = head
        count = 0
        while cur:
            count += 1
            cur = cur.next
        k = k % count
        if k == 0: return head
        left, right = head, head
        for i in range(k):
            right = right.next
        while right.next:
            left, right = left.next, right.next
        dummy = ListNode(-1)
        dummy.next = left.next
        left.next = None
        right.next = head
        return dummy.next
```
