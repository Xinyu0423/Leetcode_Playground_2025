# Solution 1
```Python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def swapNodes(self, head, k):
        """
        :type head: Optional[ListNode]
        :type k: int
        :rtype: Optional[ListNode]
        """
        h = ListNode(-1)
        h.next = head 
        p = h.next
        length = 0
        while p is not None:
            p = p.next
            length += 1
        p = h.next
        temp_p = h.next
        for i in range(k -1):
            p = p.next
        for i in range(length - k):
            temp_p = temp_p.next
        p.val, temp_p.val = temp_p.val, p.val
        return h.next
```