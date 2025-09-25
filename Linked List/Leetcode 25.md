# Solution 1
```Python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def reverseKGroup(self, head, k):
        """
        :type head: Optional[ListNode]
        :type k: int
        :rtype: Optional[ListNode]
        """
        if head is None or head.next is None:
            return head
        h = ListNode(-1)
        h.next = head
        pre = h
        tail = head
        n = 0
        while tail is not None:
            n += 1
            print(tail.val)
            if n % k == 0:
                p = pre.next
                for i in range(k - 1):
                    q = p.next
                    p.next = q.next
                    q.next = pre.next
                    pre.next = q
                tail = p.next
                pre = p 
            else:
                tail = tail.next
        return h.next
```