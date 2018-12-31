# Description
Given a sorted linked list, delete all nodes that have duplicate numbers, leaving only distinct numbers from the original list.

**Examples:**
```
Input: 1->2->3->3->4->4->5
Output: 1->2->5

Input: 1->1->1->2->3
Output: 2->3
```

# Solution:

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def deleteDuplicates(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        if not head or not head.next:
            return head
        
        dummy = ListNode(-1)
        dummy.next = head
        pre = dummy
        cur = head
        post = head.next
        
        while post:
            if cur.val == post.val:
                while post and post.val == cur.val:
                    post = post.next
                pre.next = post
                cur = post
                if post:
                    post = post.next
            else:
                pre = pre.next
                cur = cur.next
                post = post.next
        return dummy.next
```
