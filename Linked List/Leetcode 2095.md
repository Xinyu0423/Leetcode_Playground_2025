# Solution 1
```Python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def deleteMiddle(self, head):
        """
        :type head: Optional[ListNode]
        :rtype: Optional[ListNode]
        """
        h = ListNode(-1)
        h.next = head
        pre = h
        fast = h.next
        slow = h.next
        while fast is not None and fast.next is not None:
            fast = fast.next.next
            slow = slow.next
            pre = pre.next
        pre.next = slow.next
        return h.next
```
