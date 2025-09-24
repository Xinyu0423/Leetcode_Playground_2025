# Solution 1
```Python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def swapPairs(self, head):
        """
        :type head: Optional[ListNode]
        :rtype: Optional[ListNode]
        """
        if head is None or head.next is None:
            return head
        h = ListNode(-1)
        temp_h = h
        h.next = head
        p = head
        while p is not None and p.next is not None:
            a = p
            b = p.next
            next_pair = b.next
            temp_h.next = b
            b.next = a
            a.next = next_pair
            
            temp_h = a
            p = next_pair
        return h.next
```