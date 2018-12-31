# Description

Given a sorted linked list, delete all duplicates such that each element appear only once.

**Examples:**

```
Input: 1->1->2
Output: 1->2

Input: 1->1->2->3->3
Output: 1->2->3
```


# Solution 1:

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def deleteDuplicates(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        if not head or not head.next:
            return head
        
        cur = head
        post = cur.next
        
        while post:
            if post.val == cur.val:
                post = post.next
                cur.next = post
            elif post.val != cur.val:
                post = post.next
                cur = cur.next
        return head
```

# Solution 2:
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
        
        cur, post = head, head.next
        while post:
            if cur.val == post.val:
                while post and post.val == cur.val:
                    post = post.next
                cur.next = post
                cur = post
                if post:
                    post = post.next
            else:
                cur = cur.next
                post = post.next
        return head
```
