# Description
Reverse a linked list from position m to n. Do it in one-pass.

**Note:** 1 ≤ m ≤ n ≤ length of list.

**Example**
```
Input: 1->2->3->4->5->NULL, m = 2, n = 4
Output: 1->4->3->2->5->NULL
```
# Solution

```python
class Solution:
    def reverseBetween(self, head, m, n):
        """
        :type head: ListNode
        :type m: int
        :type n: int
        :rtype: ListNode
        """
        dummy = ListNode(-1)
        dummy.next = head
        cur = dummy
        for i in range(m-1):
            cur = cur.next
        p = cur.next
        for i in range(n-m):
            tmp = cur.next
            cur.next = p.next
            p.next = p.next.next
            cur.next.next = tmp
        return dummy.next
```
