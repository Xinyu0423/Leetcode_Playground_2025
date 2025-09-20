# Solution 1
```Python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def rotateRight(self, head, k):
        """
        :type head: Optional[ListNode]
        :type k: int
        :rtype: Optional[ListNode]
        """
        if k == 0 or head is None or head.next is None:
            return head
        p = head
        n = 1
        while p.next is not None:
            p = p.next
            n += 1
        p.next = head
        k = k % n
        m = n - k
        for i in range(m):
            p = p.next
            head = head.next
        p.next = None
        return head
```